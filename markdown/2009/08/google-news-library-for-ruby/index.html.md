---
layout: post
title: Google News library for Ruby
date: 2009-08-20
tags: ["Blog","code","code"]
---

I was surprised that Google News has no API, so I built my own: Using [HTTParty](http://github.com/jnunemaker/httparty/tree/master), I wrote a small Ruby library for Google News. Put this in a 'googlenews.rb' file in the /lib/ directory of your Rails application to grab google news stories and topic lists.

Haven't figured out how to get more than 10 items... Safari seems to be able to with feed://news.google.com?output=rss... but I'm not sure how.

<pre>
gem "httparty"
require "httparty"

class Googlenews
  include HTTParty
  base_uri 'news.google.com'

  def self.items
    options = { :query => { :output => 'rss' } }
    features = self.get('/news', options)
    features['rss']['channel']['item']
  end

  def self.extract_topic(item)
    # ncl=duPfj30A5WoxBHMupoOtlciO1jY1M&
    item['description'].match(/ncl=([a-zA-Z0-9]+)&/)[1]
  end

  def self.topic(item)
    options = { :query => { :output => 'rss', :ncl => self.extract_topic(item) } }
    features = self.get('/news/more', options)
    features['rss']['channel']['item']
  end

  # store in database (unused)
  # def self.story(item)
    # item['category']
    # item['title']
    # item['guid']
    # item['description']
    # item['link']
    # item['pubDate']

    # t.string :category, :default => ''
    # t.string :title, :default => ''
    # t.string :guid, :default => ''
    # t.text :description, :default => ''
    # t.string :link, :default => ''
  # end

end
</pre>

Once you've dropped this in /lib/, you can use it  in a Rails controller like this (I needed JSON, to work with the feed in JavaScript):

<pre>
class DataController < ApplicationController

  def latest
    render :json => Googlenews.items
  end

end

</pre>

_**Update:** to get more than 10 items, add a GET parameter 'num=20' to the feed URL. This works both for topic and for the main feed. I haven't confirmed this but I think it's still limited to 30 items. Again, Safari manages to get more, but perhaps it does repeated queries. Still investigating. Anyways, that makes it:
_
<pre> def self.items
    options = { :query => { :output => 'rss', :num => '20' } }
    features = self.get('/news', options)
    features['rss']['channel']['item']
  end </pre>

_**Update:** This now has a real home on Github, where it's called [ruby-googlenews](http://github.com/jywarren/ruby-googlenews)._