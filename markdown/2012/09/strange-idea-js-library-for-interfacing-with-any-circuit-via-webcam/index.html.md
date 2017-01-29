---
layout: post
title: Strange idea: JS library for interfacing with any circuit via webcam
date: 2012-09-09
tags: ["code"]
---

I've been pondering the odd way that our use of a webcam in the [PLOTS spectrometer](http://publiclaboratory.org/tool/spectrometer) allows connecting directly from HTML5/JavaScript to a spectrometer over USB. What if we used a standardized array of LEDs -- say, an Arduino shield of 'em -- in a dark box facing a webcam. And wrote a standardized library for reading analog & digital pins from the video output... You could then plug many different circuits directly into a webpage.