---
layout: post
title: Cartagen 0.6.1 - Speed
date: 2009-07-29
tags: ["Blog","cartagen","cartagen","code","gss","map rendering","mapping"]
---

[![](http://unterbahn.com/wp-content/uploads/farm3.static.flickr.com/2621/3768712061_5506f2ff96.jpg)](http://cartagen.org)

We know we just released Cartagen 0.5 a couple weeks ago, but after testing it extensively in the wild, we really wanted a fast, low-resource release so that users of netbooks, older computers, and older browsers could use Cartagen too. 

So, as well as including some general cleanup, this version hums along on a variety of machines. Please send feedback on speed/load times/CPU usage, etc; we tested it on an 800mhz G4 iMac and while it wasn't super responsive, it did load and was somewhat usable in Firefox 3.5. For reference, Hulu.com's Flash player does not run on that machine. On more powerful machines (4x3ghz Intel Xeon, 2500x1600 monitor), it can load over 10,000 objects in the viewport without hiccuping. For most users, a typical browser window size yields a responsive and reasonably low-resource experience. 

[Download Cartagen 0.6.1](http://code.google.com/p/cartagen) (We did 0.6 and just rushed directly into 0.6.1 before announcing.)

There's definitely a lot more we can do to improve speed, but for now we feel good about our optimizations. We identified the high CPU usage as generally poor management of timers in JavaScript, and wrote a TimerManager class which adjusts its timer intervals automatically, easing the CPU load. We elected to maintain a relatively high CPU usage to keep things rendering smoothly,  but users of TimerManager can 'turn up the heat' or turn down CPU usage by tweaking a 'spacing' parameter. We also broke more intense tasks up by creating a TaskManager class, which preserves UI responsiveness and framerate while staying in a single JavaScript thread. We plan to use the multithreaded, asynchronous Web Workers spec in HTML5 when available, but for now we wanted to work on older hardware/software. 

We hope that TimerManager and TaskManager will be of use to others working with JavaScript animation and we'll be packaging them up separately for download.

For now, look at [http://code.google.org/p/cartagen](http://code.google.org/p/cartagen) for source and [http://wiki.cartagen.org](http://wiki.cartagen.org) for update docs.