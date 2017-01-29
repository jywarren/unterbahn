---
layout: post
title: Adjustment for Rails 'find()' method
date: 2009-08-29
tags: ["Blog","code"]
---

Rails performs an SQL SELECT statement like "SELECT * FROM table_name WHERE table_name.id IN (1,2,3,4,5)" when its .find() method is passed an array of IDs. But it fails if one of those ids is not found. Sometimes it's useful to find all _available_ records, but not fail if not all are found. I adjusted the search for this scenario in my working copy of the OpenStreetMap Rails port:

<pre>
# @nodes += Node.find(nodes_to_fetch, :include => :node_tags)
@nodes += Node.find(:all,:conditions => ["id IN ("+nodes_to_fetch.join(',')+")"], :include => :node_tags)
</pre>