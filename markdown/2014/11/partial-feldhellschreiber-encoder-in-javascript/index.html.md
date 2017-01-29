---
layout: post
title: Partial Feldhellschreiber encoder in JavaScript
date: 2014-11-30
tags: ["Blog","code","hellschreiber"]
---

Noah Vawter (of [Exertion Instruments](http://exertion.pbworks.com/)) and I used to send each other voicemails encoded in a [pre] Nazi-era (OK, further research shows it was developed in the 1920's) German radio protocol called [Hellschreiber](https://en.wikipedia.org/wiki/Hellschreiber) or Feldhellschreiber, invented by Rudolph Hell. It's a sort of early paper-tape teletype system which was also the first example of bitmapped fonts. You can encode/decode using **fldigi** (available on apt in ubuntu and here: [http://w1hkj.com/Fldigi.html](http://w1hkj.com/Fldigi.html)). Despite its unfortunate origins, it's pretty interesting as an early automated text-over-radio system which is robust mainly for the same reason people are good at reading CAPTCHAs.

Here's a mechanical feldhellschreiber machine in red/blue stereo: [http://unterbahn.com/2011/04/franks-n4spp-hellschreiber-page/](http://unterbahn.com/2011/04/franks-n4spp-hellschreiber-page/)

Anyways, Noah and I had always wanted to do an implementation in JavaScript, and created this repo long ago: [https://github.com/jywarren/hellschreiber-js](https://github.com/jywarren/hellschreiber-js)

Finally got around to more coding this weekend, and put together part of an encoder, a bit messily but short enough to be readable. You can try it out here:

[http://jywarren.github.io/hellschreiber-js/](http://jywarren.github.io/hellschreiber-js/)

It doesn't work.

[![feldhellschreiber](feldhellschreiber-1024x575.png)](http://unterbahn.com/wp-content/uploads/2014/11/feldhellschreiber.png)

Well, it does make noise, and write out letters how you'd expect them to appear in **fldigi** -- but it's not anywhere near synced and I'm struggling with adjusting the length and latency of the sound sample -- generated in JS using [riffwave.js](http://www.codebase.es/riffwave/) as well as the setInterval of the script itself, which ought to run once per pixel. I'm also hobbled by using an awfully-encoded hellschreiber font from the **fldigi** source, which I refactored into JavaScript, but which is inexplicably stored as hex values in **rows** instead of **columns**, when Hellschreiber is an innately column-based format. But I don't think that's the limiting factor.

I'm starting to get diminishing returns for my debugging and am pretty tired, so I'm just going to put this out there and think on it and/or see if I can get help from someone who's a bit more methodical of a coder. Sometimes I'm a bit too much of an empiricist, not to mention a cobbler-together, impatient as I am to get to Hello World.

Also -- once I get an encoder working, I really want to move on to a decoder, so you can run this on a phone facing another phone, and send/receive messages that way. How efficient and historically accurate!