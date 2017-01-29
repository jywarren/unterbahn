---
layout: post
title: Use Google satellite imagery to rectify on Map Warper
date: 2009-11-12
tags: ["Blog","kibera","mapping"]
---

I've been taking very high-res imagery from a weather balloon and rectifying it, but the OpenStreetMap data isn't detailed enough to find rectifying points... the result is a bit like this:

[![](4095876121_34cc4ab695.jpg)](http://www.flickr.com/photos/jeffreywarren/4095876121/)

To add a Google layer, just run:

<pre>to_map.addLayer(googleSat,{'maxZoomLevel':22});</pre>

or drag this bookmarklet into your browser bookmarks bar, and click the bookmark when you're on the Rectify page:

[google-for-warper](javascript:to_map.addLayer(googleSat,{)

The result is something like this:

[![](4099000850_f6f0dce4ed.jpg "kibera")](http://www.flickr.com/photos/jeffreywarren/4099000850/)