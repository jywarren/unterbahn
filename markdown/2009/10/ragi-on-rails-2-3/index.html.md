---
layout: post
title: RAGI on Rails 2.3+
date: 2009-10-28
tags: ["code"]
---

[RAGI](http://www.snapvine.com/code/ragi/), a Ruby interface for Asterisk, allows you to handle phone calls with a Ruby on Rails application. The config/environment.rb entry has to be modified a bit for a modern Rails, since many online tutorials/resources were written in the Rails ~1.2 era, and assume WEBrick as the server. 

The offending line is this:
<pre>class SimpleThreadServer < WEBrick::SimpleServer</pre>

Which can be modified to:

<pre>class SimpleThreadServer < Mongrel::HttpHandler</pre>

The complete configuration you'll need to add inside your **Rails::Initializer.run do 'config'** block is:

<pre>  # The following code tells Rails to start a Ragi server
  # as a separate thread.
  ActiveSupport::Dependencies.mechanism = :require
  # Include your application configuration below
  # Simple server that spawns a new thread for the server
  class SimpleThreadServer < Mongrel::HttpHandler
    def SimpleThreadServer.start(&block)
      Thread.new do block.call
      end
    end
  end
  require 'ragi/call_server'
  RAGI::CallServer.new( :ServerType => SimpleThreadServer )
</pre>