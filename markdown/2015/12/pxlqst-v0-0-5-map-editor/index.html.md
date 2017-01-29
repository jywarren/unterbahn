---
layout: post
title: Pxlqst v0.0.5 - map editor
date: 2015-12-27
tags: ["Blog","code","pxlqst","pxlshp"]
---

[![Screenshot 2015-12-27 at 11.38.22 AM](http://unterbahn.com/wp-content/uploads/2015/12/Screenshot-2015-12-27-at-11.38.22-AM.png)](Screenshot-2015-12-27-at-11.38.22-AM.png)

I released a new version of [Pxlqst](http://pxlqst.com), my [16x16 dungeon adventure game](https://github.com/jywarren/pxlqst) (pictured above), and report in the [release notes](https://github.com/jywarren/pxlqst/releases) that:

*   doors can now lead to new rooms
*   new format for storing room "maps" as collections of strings
*   updated README instructions for world generation and map editing
*   **Known bug:** cake no longer nutritious :-(
*   fewer dependencies
*   rooms can be "slept" and "woken"

This is still not quite playable, but things are coming together enough that, once I get combat and inventory running, I think it'll be possible to build a simple quest. I have been thinking about the separation between Pxlqst, the game, and Pxlngn, the game engine, upon which I expect pixel art enthusiasts will create many a 16x16 adventure game.

See the map format here:

[![Screenshot 2015-12-27 at 8.10.12 AM](http://unterbahn.com/wp-content/uploads/2015/12/Screenshot-2015-12-27-at-8.10.12-AM.png)](Screenshot-2015-12-27-at-8.10.12-AM.png)