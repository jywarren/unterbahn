---
layout: post
title: gdalwarp cannot perform perspectival distortion
date: 2010-07-27
tags: ["Blog","bugs","cartagen","code","knitter"]
---

[![](http://unterbahn.com/wp-content/uploads/2010/07/failed-warp.png "failed-warp")](failed-warp.png)

I've been banging my head against a wall for a few days on this one, first struggling with ImageMagick, then switching to gdal to get full-resolution geoTIFFs from [Cartagen Knitter](http://cartagen.org/maps). I had a 'duh' moment just now when I realized that gdalwarp can only do polynomial or thin plate spline warps, neither of which are what I want - that is, perspectival warping. I want to map 4 corner ground control points or GCPs to four latitude/longitude positions. Back to ImageMagick...

_I know there are 5 GCPs in the image above - it was the same deal with just 4... it can't do more than a shear unless you either add the minimum 6 GCPs for a single polynomial warp, or go for  a thin plate spline (TPS) distort. A good way to think about TPS is as if the image were a sheet of thin metal (the reason it's called a TPS) and that you're bending it in the z-dimension, aplanar. This causes funny curved edges and is not what I'm looking for._

_OK, one more note for future reference: see [this page](http://docs.bentley.com/en/I-RASB/irasbhelp171.html) for a discussion of different warping techniques and also for the minimum number of GCPs required for different-order polynomial warps._