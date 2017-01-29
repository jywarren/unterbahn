---
layout: post
title: Installing Java 1.4.x on Snow Leopard
date: 2009-10-10
tags: ["code"]
---

[OneSwarm's](http://oneswarm.cs.washington.edu/) wiki ([link](http://wiki.oneswarm.org/index.php/OS_X_10.6_Snow_Leopard)) covers some easy steps for installing Java 1.4 on Snow Leopard. I needed it to get the MPowerPlayer SDK running so I could compile some code for Java-enabled mobile phones. Thanks to [wheremydogs.at](http://wheremydogs.at/index_files/fixing-the-preverifier-build-error-for-mpowerplayer-on-mac-os-x.php) for pointing out that MPowerPlayer relies on some Java 1.4 classes.

<pre>cd /tmp/
wget [http://www.cs.washington.edu/homes/isdal/snow_leopard_workaround/java.1.4.2-leopard.tar.gz](http://www.cs.washington.edu/homes/isdal/snow_leopard_workaround/java.1.4.2-leopard.tar.gz "http://www.cs.washington.edu/homes/isdal/snow_leopard_workaround/java.1.4.2-leopard.tar.gz")
tar -xvzf java.1.4.2-leopard.tar.gz
sudo mv 1.4.2 /System/Library/Frameworks/JavaVM.framework/Versions/1.4.2-leopard
cd /System/Library/Frameworks/JavaVM.framework/Versions/
sudo ln -s 1.4.2-leopard 1.4
open "/Applications/Utilities/Java Preferences.app"
</pre>

For those of you also working with MPowerPlayer, the error I was getting is:

<pre>
  $ ant
  Buildfile: build.xml

  compile:

  preverify:
       [exec] Error preverifying class java.lang.Class
       [exec]     VERIFIER ERROR java/lang/Class.newInstance0()Ljava/lang/Object;:
       [exec] Illegal type in constant pool
       [exec] Result: 1

  package:

  BUILD SUCCESSFUL
  Total time: 1 second</pre>

But now that I have Java 1.4, it's compiling fine.