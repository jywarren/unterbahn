---
layout: post
title: Haversine formula in JavaScript
date: 2008-12-03
tags: ["Blog","code"]
---

_Given a start point, initial bearing, and distance, this will calculate the destination point and final bearing travelling along a (shortest distance) great circle arc:_
<pre>var lat2 = Math.asin( Math.sin(lat1)*Math.cos(d/R) + 
                      Math.cos(lat1)*Math.sin(d/R)*Math.cos(brng) );
var lon2 = lon1 + Math.atan2(Math.sin(brng)*Math.sin(d/R)*Math.cos(lat1), 
                             Math.cos(d/R)-Math.sin(lat1)*Math.sin(lat2));</pre>

- [Calculate distance and bearing between two Latitude/Longitude points using Haversine formula in JavaScript](http://www.movable-type.co.uk/scripts/latlong.html)