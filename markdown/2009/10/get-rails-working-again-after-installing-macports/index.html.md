---
layout: post
title: Get Rails working again after installing MacPorts
date: 2009-10-09
tags: ["Blog","code"]
---

Mac Rails developers: I installed MacPorts to get RMagick, and it installed a new version of Ruby, without RubyGems. This meant that when I typed **script/server**, it claimed that:

"Rails requires RubyGems >= . Please install RubyGems and try again: http://rubygems.rubyforge.org"

MacPorts had added some crap to my PATH variable. If you edit your ~/.profile you'll see this line:

`export PATH=/opt/local/bin:/opt/local/sbin:$PATH`

Just change that to:

`export PATH=$PATH:/opt/local/bin:/opt/local/sbin`

Then open a NEW shell prompt, i.e. a new Terminal window (this reloads the PATH variable)...

...and it'll find your _OLD_ version of Rails before the new MacPorts one, and things will work normally. You can confirm by typing "which ruby" in the terminal, and you should see "/usr/bin/ruby" NOT "/opt/local/bin/ruby".