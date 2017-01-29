---
layout: post
title: Vectorizing sketches and photos with your smartphone/web browser
date: 2015-08-11
tags: ["Blog","vectors"]
---

[![IMG_8462](IMG_8462-1024x768.jpg)](http://unterbahn.com/wp-content/uploads/2015/08/IMG_8462.jpg)

Yesterday I wrote [VectorCam](), building on the [excellent excellent imagetracerjs library](https://github.com/jankovicsandras/imagetracerjs) by András Jankovics. Source AGPLv3 at https://github.com/jywarren/vectorcam.

This is a pure JavaScript raster-to-vector converter, which takes images (png, jpg, gif?) and traces them into downloadable SVGs (I haven't tried a conversion to PDF or DXF, but that'd be useful).

With it, you can snap a photo with your phone, and immediately vectorize it for use in print, laser cutting, or [desktop paper cutting](http://publiclab.org/notes/warren/07-30-2015/silhouette-cameo-desktop-paper-cutter-for-prototyping). I always thought this should exist as a web service, since it can be a pain to open up Inkscape sometimes, and this is supposed to be a pretty well-solved problem.

It works on Android, fastest in Chrome - and only on Safari on iOS, probably due to Apple's closed-browser strategy.

Here's a snap of the output from the above image, opened in Inkscape to show the vector lines:

[![Selection_001](Selection_001-1024x485.png)](http://unterbahn.com/wp-content/uploads/2015/08/Selection_001.png)

András' library does a fantastic job; all I did was connect it to a file upload form and ensure the SVG downloads well, and make a nice interface with a settings dialog. This last could be expanded, as well.

<iframe height="500px" width="100%" style="border:0;" src="http://jywarren.github.io/vectorcam/"></iframe>