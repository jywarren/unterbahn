---
layout: post
title: Warcraft map stylesheet for London
date: 2009-07-24
tags: ["Blog","cartagen","gss","warcraft"]
---

So this is an accurate (in terms of coordinates) map of London, generated from [OpenStreetMap](http://OpenStreetMap.org) data:

[field name="iframe"]

You can pan around quite a bit and use the scroll wheel to zoom. To achieve this, I created the following [geographic stylesheet](http://wiki.cartagen.org):

`[http://unterbahn.com/cartagen/warcraft.gss](http://unterbahn.com/cartagen/warcraft.gss)`

The map is built on Cartagen, a mapping framework for viewing and geographic data in a dynamic, personally relevant way. Cartagen uses the GSS (Geo Style Sheet) format, which allows users to design maps with CSS-like styles. Learn more at [Cartagen.org](http://cartagen.org) and [the Cartagen wiki](http://wiki.cartagen.org/), or download the source at [Google Code](http://code.google.com/p/cartagen).

Go to [Cartagen.org](http://cartagen.org?gss=http://unterbahn.com/cartagen/warcraft.gss) to view anywhere in the world through this stylesheet.

Dabu!

_**Quick update:** some users (read: most) are having trouble zooming in and out! This is because of a known last-minute bug in the 0.6 release of Cartagen, and only affects maps embedded in other pages. It does not affect [cartagen.org](http://cartagen.org?gss=http://unterbahn.com/cartagen/warcraft.gss). For a quick fix, to zoom **you can also hold down the 'z' key and drag up and down on the map.**
__**Followup update:** zooming with the scroll wheel should work now. Thanks for your patience!
_