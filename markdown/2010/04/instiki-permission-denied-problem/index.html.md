---
layout: post
title: Instiki 'Permission denied' problem
date: 2010-04-13
tags: ["Blog","code"]
---

I run a [few](http://wiki.cartagen.org) Instiki [sites](http://wiki.grassrootsmapping.org) on [Phusion Passenger](http://www.modrails.com/), and they occasionally break - namely, they give a 'Permission denied' message which is hard to track.

The problem is that there are temp files like `/tmp/passenger.1234` which have some kind of permissions problem. 

To resolve this, you can simply delete those files, like with:

`sudo rm -r /tmp/passenger*`

and reboot Instiki (Apache, really):

`sudo apachectl graceful`