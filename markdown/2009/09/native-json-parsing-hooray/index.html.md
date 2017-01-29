---
layout: post
title: Native JSON parsing... hooray, with benchmarks!
date: 2009-09-27
tags: ["Blog","cartagen","code"]
---

I just tested the native JSON parser in Safari (this is also implemented in Firefox now, and IE8) and it dramatically speeds up the parsing of [Cartagen's](http://cartagen.org) JSON data files! Take a look at these times for parsing six typical data plots in milliseconds:

_**prototype.js's .evalJSON():**
parsed: 43
parsed: 7
parsed: 47
parsed: 63
parsed: 37
parsed: 53
**Native JSON.parse():**
parsed: 8
parsed: 6
parsed: 6
parsed: 9
parsed: 5
parsed: 7
_

That's a sixfold improvement!

And for Firefox 3.5:

_**prototype.js's .evalJSON():**
parsed: 174
parsed: 157
parsed: 198
parsed: 349
parsed: 155
parsed: 455
parsed: 323
parsed: 276
parsed: 272
**Native JSON.parse():**
parsed: 13
parsed: 13
parsed: 14
parsed: 20
parsed: 12
parsed: 25
parsed: 20
parsed: 18
parsed: 18
_

That's more than 15 times the speed! 