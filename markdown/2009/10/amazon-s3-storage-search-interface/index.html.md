---
layout: post
title: Amazon s3 storage search interface
date: 2009-10-07
tags: ["cloud computing","code"]
---

I use Amazon S3 for backup, and find that it's hard to use because there's no search function, so I can't see what I've backed up.

So, I extended s3cmd.rb (comes with the WONDERFUL [s3cmd.rb rsync clone](http://s3sync.net/wiki) for Amazon S3) with a search command.

Now I can use s3sync.rb to rsync my files up, then type:

> s3sync.rb search bucket_name:path/to/restrict/search search_term

and I get, for example:

> backup/2009/spatial/jeff-spatial-vertical.key> 
> backup/2009/spatial/spatial-assignment-1-jeff.pdf> 
> backup/2009/spatial/spatial-assignment-1.key> 
> backup/2009/spatial/spatial-assignment-1.key.zip> 
> backup/2009/spatial/spatial-interface> 
> backup/2009/spatial/spatial-lecture-1> 
> backup/2009/spatial/spatial-lecture-1.key> 
> backup/2009/spatial/spatial-lecture-1.key.zip> 
> backup/2009/spatial/spatial-lecture-1/spatial-lecture-1.key> 
> backup/2009/spatial/spatial-lecture-1/spatial-lecture-1.pdf> 
> backup/2009/spatial/spatial-lecture-3.key> 
> backup/2009/spatial/spatial-lecture-3.mov> 
> backup/2009/spatial/spatial-lecture-3.pdf> 
> backup/2009/spatial/spatial-uploads> 
> backup/2009/spatial/spatial-wayfinding.key> 
> you just spent 6.0e-05 cents

The last line is because the price of making a list request in s3 is $0.01 per 1000 requests in the US; so I thought it'd be a good idea to tell people how much they're spending. 

I'll try to commit this to the main s3sync.net codebase, but for now you can just download it here: [s3sync](http://unterbahn.com/wp-content/uploads/2009/10/s3sync.zip)