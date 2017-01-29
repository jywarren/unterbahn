---
layout: post
title: Object.hasOwnProperty() in JavaScript
date: 2010-11-07
tags: ["code","code"]
---

On [StackOverflow](http://stackoverflow.com/questions/208016/how-to-list-the-properties-of-a-javascript-object), user Pablo Cabrera points out:

> As slashnick pointed out, you can use the "for in" construct to iterate over an object for its attribute names. However you'll be iterating over all attribute names in the object's prototype chain. If you want to iterate only over the object's own attributes, you can make use of the Object#hasOwnProperty() method. Thus having the following.
> 
> for (var key in obj) {
>     if (obj.hasOwnProperty(key)) {
>         /* useful code here */
>     }
> }

Wish I'd known of that a year ago.