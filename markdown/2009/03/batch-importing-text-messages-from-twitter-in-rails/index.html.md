---
layout: post
title: Batch importing text messages from Twitter in Rails
date: 2009-03-10
tags: ["code","mapping","nocollision","sms","tutorial","Tutorials","twitter","whooz"]
---

Here we actually batch import the messages, saving them in a local model. I also demonstrate a script to perform the imports, and set up a table to store key:value pairs for more advanced usage - I'll finish that feature up in a subsequent tutorial.

Saving the messages locally is important for not exceeding the Twitter rate limit, as well as for performing more complex searches and manipulations with the data. It also provides a common message storage if you're importing from multiple sources, say, [FrontlineSMS](http://www.frontlinesms.com/), [Clickatell](http://clickatell.com), and Twitter.

<object width="500" height="313"><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="moogaloop.swf?clip_id=3560955&server=vimeo.com&show_title=1&show_byline=1&show_portrait=0&color=ffffff&fullscreen=1" /><embed src="http://vimeo.com/moogaloop.swf?clip_id=3560955&server=vimeo.com&show_title=1&show_byline=1&show_portrait=0&color=ffffff&fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="500" height="313"></embed></object>  
[WHOOZ Tutorial: Importing text messages from Twitter to Ruby on Rails](http://vimeo.com/3560955).

Download the code for this tutorial here: [whooz-messages-table-batch-importing.zip](http://unterbahn.com/wp-content/uploads/2009/03/whooz-messages-table-batch-importing.zip) (LGPL 3.0) or on [Google Code](http://code.google.com/p/whooz/)

This builds on the code written in the last tutorial, [Sending and receiving text messages in Rails with Twitter](http://unterbahn.com/2009/03/connecting-a-ruby-on-rails-application-to-twitter/)

I know this is pretty low resolution, but I'll upload an HD version next week; Vimeo allows only one HD clip per week.