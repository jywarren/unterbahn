---
layout: post
title: Fixing Cache Images plugin in Wordpress on MediaTemple
date: 2010-01-24
tags: ["code"]
---

Matt Mullenweg's great [Cache Images plugin](http://svn.wp-plugins.org/cache-images/trunk/) for WordPress (Just go to the Plugins > Add New page in your WordPress install and search for it) lets you copy any hotlinked images on your blog into your own /uploads/ folder for safekeeping (and to be polite to others' servers!), and I love it. But when you first install it, it often chokes, especially on MediaTemple. I've had problems with this more than once, so I thought I'd jot this down for future reference and to help anyone else struggling with the same issues. The two problems are a) permissions for the /uploads/ folder, and b) the file_get_contents() function. Here's a fix:

First, you have to change the uploads directory from a long absolute path to just a relative one, so in Settings > Miscellaneous, instead of:

`/bla/bla/mediatemples/long/url/domainname/html/wp-content/uploads/`

it should say:

`wp-content/uploads`

Second, you have to change the file_get_contents() call on line 118 of the plugin file "plugins/cache-images/cache-images.php". MediaTemple and other hosts don't like that. But you can usually use the curl() library, so if you add the following code somewhere near the top of the file, you can use this fancy new '**file_get_contents_curl()**' function instead of the native one:

<pre>
function file_get_contents_curl($url) {
	$ch = curl_init();

	curl_setopt($ch, CURLOPT_HEADER, 0);
	curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1); //Set curl to return the data instead of printing it to the browser.
	curl_setopt($ch, CURLOPT_URL, $url);

	$data = curl_exec($ch);
	curl_close($ch);

	return $data;
}
</pre>

Then all you have to do is change the call (on what USED TO BE line 118) to:

<pre>$img      = file_get_contents_curl( $b['scheme'] . '://' . $b['host'] . str_replace(' ', '%20', $b['path']) . $b['query'] );</pre>

That is, just change "file_get_contents" to "file_get_contents_curl()".

I'd do it myself for you and host the file, but it's not my code. Hmm, can I commit this change anywhere? Matt?