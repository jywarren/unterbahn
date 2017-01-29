---
layout: post
title: Instiki: add an auto redirect to the default web
date: 2010-03-04
tags: ["code"]
---

I have a few Instiki instances out there: [wiki.grassrootsmapping.org](http://wiki.grassrootsmapping.org) and [wiki.cartagen.org](http://wiki.cartagen.org) - and the Grassroots Mapping wiki now has two 'webs'. Initially when I added a second web, the front page at wiki.grassrootsmapping.org began showing a list of webs instead of the HomePage of the main web... if you're an Instiki user you'll know what I'm talking about. You can see the page I saw here: [wiki.grassrootsmapping.org/web_list](http://wiki.grassrootsmapping.org/web_list)

Instiki allows you to define a DEFAULT_WEB in your **/config/environment.rb**, but it won't redirect the web root to that web's HomePage, which would seem to be the point. Darn. So I [forked and patched Instiki on Github](http://github.com/jywarren/instiki), adding the following code to replace line 26 of **/app/controllers/wiki_controller.rb**:

<pre>      if defined? DEFAULT_WEB
        @web_name = DEFAULT_WEB
        redirect_home
      else
        redirect_to :action => 'web_list'
      end
</pre>

Now if I go to [wiki.grassrootsmapping.org](http://wiki.grassrootsmapping.org), I see the HomePage of my default web. Hooray!

_**Update:** OK, my bad. This is unnecessary:_

As **distler** [pointed out on Github](http://github.com/jywarren/instiki/commit/fc88bc64e47bd92068058ddb5e41b45f49c7a2c4#comments), defining DEFAULT_WEB should work out of the box. Why didn't it work for me, I wondered?

Well, I put the line:

<pre>DEFAULT_WEB = 'wiki'</pre>

in environment.rb, but I put it OUTSIDE the **Rails::Initializer.run do 'config'** block. Putting that line inside that code block solved my problem.   

I'm leaving this all up for future generations to learn from my mistakes. (Most likely me in a year or so.)