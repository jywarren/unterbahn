---
layout: post
title: Solution for when Git thinks everything has been modified
date: 2011-06-30
tags: ["Blog"]
---

Steven Robbins figured out that some git clients mess with filemodes. You can tell git not to pay attention to them with:

<pre>
git config --global core.filemode false
git config core.filemode false
</pre>

[http://www.grumpydev.com/2011/01/19/switching-from-cygwin-to-msysgit-git-thinks-everything-has-been-modified/](http://www.grumpydev.com/2011/01/19/switching-from-cygwin-to-msysgit-git-thinks-everything-has-been-modified/)

Thank gott.