---
layout: post
title: Ruby singleton classes explained
date: 2010-04-06
tags: ["Blog"]
---

I've become used to JavaScript (gasp! cringe!) in writing [Cartagen](http://cartagen.org) and sometimes find myself wanting to assign arbitrary attributes to objects I just made up. Unfortunately this JavaScript code:

<pre>var new_object = { we: 'can', make: 'up', any: 'thing' }</pre>

doesn't work in Ruby:

<pre>new_object = {}
new_object.latitude = 'lalalala'</pre>

It yields: 

<pre>undefined local variable or method `latitude' for []:Array</pre>

But you can create what are called 'singleton objects', as described on [contextualdevelopment.com](http://www.contextualdevelopment.com/articles/2008/ruby-singleton):

<pre>foobar = Array.new

def foobar.size
  "Hello World!"
end

foobar.size  # => "Hello World!"
foobar.class # => Array</pre>

Hooray!