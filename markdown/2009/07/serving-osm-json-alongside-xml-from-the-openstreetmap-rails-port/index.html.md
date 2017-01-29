---
layout: post
title: Serving 'OSM-JSON' alongside XML from the OpenStreetMap Rails port
date: 2009-07-31
tags: ["Blog","cartagen","cartagen","code","mapping","openstreetmap","rails","Tutorials"]
---

[OpenStreetMap.org](http://openstreetmap.org)'s RESTful API allows anyone to access data on their continually growing collaborative map of the world... in XML. This is great for most applications, but if you're working in JavaScript (as [we are](http://cartagen.org)), XML might as well be greek. We need JSON.

To offer OSM-JSON along with of OSM-XML, we added a route to accept a ".format" suffix, and split up the render call based on the params[:format] part of the route:

<pre>
# /config/routes.rb:46-50

map.connect "api/#{API_VERSION}/geohash/:geohash.:format", :controller => 'api', :action => 'geohash'
map.connect "api/#{API_VERSION}/geohash/:geohash", :controller => 'api', :action => 'geohash'

map.connect "api/#{API_VERSION}/map.:format", :controller => 'api', :action => 'map'
map.connect "api/#{API_VERSION}/map", :controller => 'api', :action => 'map'
</pre>

Notice we also added a 'geohash' route. Whereas the /map call requires a bbox parameter ('bbox=min_lon,min_lat,max_lon,max_lat'), we can use a [geohash](http://en.wikipedia.org/wiki/Geohash) ([Geohash in JavaScript](http://github.com/davetroy/geohash-js/tree/master), [Geohash in Rails](http://github.com/davetroy/geohash/tree/master)) which defines a bounding box as a sequence of letters and numbers. This fits Cartagen's needs well, and since it doesn't require any parameters, we can page cache it in Rails. (Remember that page caching bypasses Rails entirely, letting Apache handle these cached files at high speed - that saved us when we were on BoingBoing).

<!--more-->

We then modify the api_controller to respond_to either **.xml** or **.json**:

<pre>
# /app/controllers/api_controller.rb:284-287

respond_to do 'format'
  format.xml  { render :text => doc.to_s, :content_type => "text/xml" }
  format.json  { render :json => {'osm' => doc} }
end
</pre>

However, to pack up our objects into JSON properly, we also had to modify the map method further, for nodes, ways, and relations:

<pre>
# /app/controllers/api_controller.rb:186-190
if params[:format] == 'json'
  doc['node'] << node.to_json_obj
else
  doc.root << node.to_xml_node(changeset_cache, user_display_name_cache)
end
</pre>

The above was repeated for ways and relations, lines 202 and 270. 

Then, we added a geohash method to catch our new geohash route:

<pre>
# /app/controllers/api_controller.rb:76-80
def geohash
  _bbox = GeoHash.decode_bbox(params[:geohash])
  params['bbox'] = _bbox[0][1].to_s+','+_bbox[0][0].to_s+','+_bbox[1][1].to_s+','+_bbox[1][0].to_s
  map
end
</pre>

Finally, we cloned the to_json_obj methods in /models/node.rb, /models/way.rb, and /models/relation.rb, which was pretty minor - we just restructured how they're packed up.

As HTML5 and the new generation of JavaScript interpreters transform the web, I expect we'll see a lot more APIs implemented in JSON as well as XML, and I'd be happy to help anyone with an OSM Rails port get this set up. For the time being, feel free to use our OSM API (with JSON!) at http://cartagen.org/api/0.6/...

_Download the modified code here: [openstreetmap.zip](http://unterbahn.com/wp-content/uploads/2009/07/openstreetmap.zip)   
(based on OSM revision 15115)_