---
layout: post
title: Parsing out key:value pairs from text messages and geocoding them
date: 2009-04-05
tags: ["Blog","code"]
---

In this third tutorial, we scrape the incoming text messages for pairings of strings in the format "key:value value ...", which we parse out with a regular expression and store in a separate Keyvalue table. This allows us to intelligently search and manipulate the data, as well as to geocode addresses submitted along with data. This yields latitude & longitude data for a given text message.

<object width="500" height="313"><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="moogaloop.swf?clip_id=3991942&server=vimeo.com&show_title=1&show_byline=1&show_portrait=0&color=ffffff&fullscreen=1" /><embed src="http://vimeo.com/moogaloop.swf?clip_id=3991942&server=vimeo.com&show_title=1&show_byline=1&show_portrait=0&color=ffffff&fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="500" height="313"></embed></object>  
[WHOOZ Tutorial: Parsing out key:value pairs from text messages and geocoding them](http://vimeo.com/3991942).

Download the code for this tutorial here: [whooz-keyvalue-tutorial.zip](http://whooz.googlecode.com/files/whooz-keyvalue-tutorial.zip) (LGPL 3.0)

This builds on the code written in the last tutorial, [Batch importing text messages from Twitter in Rails](http://unterbahn.com/2009/03/batch-importing-text-messages-from-twitter-in-rails/)