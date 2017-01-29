---
layout: post
title: GSS hover and mouseDown selectors in Cartagen
date: 2009-05-04
tags: ["Blog","cartagen","cartagen","nocollision"]
---

Take a look at http://cartagen.org - the buildings now have both hover and mouseDown styles. The syntax is:

<pre>building: {
	lineWidth: 0.001,
	fillStyle: "#444",
	hover: {
		fillStyle: '#222'
	},
	mouseDown: {
		lineWidth: 4,
		strokeStyle: "red"
	}
},
</pre>