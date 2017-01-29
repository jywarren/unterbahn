---
layout: post
title: Tidying up Cartagen a bit with tips from dev.opera.com
date: 2010-01-31
tags: ["code"]
---

[dev.opera.com](http://dev.opera.com/articles/view/efficient-javascript/?page=2) has a great series of tips for improving JavaScript performance. Example:

> ### Use strings accumulator-style
> 
> String concatenation can be an expensive process. Using the "+" operator does not wait for the result to be assigned to a variable. Instead, it creates a new string in memory, assigns its result to that string, and it is that new string that may be assigned to a variable. The following code shows a common assignment of a concatenated string:
> 
> "a += 'x' + 'y';"> 
> 
> That code would be evaluated by firstly creating a temporary string in memory, assigning the concatenated value of 'xy', then concatenating that with the current value of "a", and finally assigning the resulting value of that to "a". The following code uses two separate commands, but because it assigns directly to "a" each time, the temporary string is not used. The resulting code is around 20% faster in many current browsers, and potentially requires less memory, as it does not need to temporarily store the concatenated string:
> 
> a += 'x';> 
> a += 'y';