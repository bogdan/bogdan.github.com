---
layout: post
title: "Finally get rid of WordPress and PHP"
published: false
tags:
- jekyll
- wordpress
- php
- migration
- liquid
---

After a few tries migrate this blog to programming language I know well, I finally found 
[jekyll](http://github.com/mojombo/jekyll) - lightweight static site generator. My main concerns in this choice was:

* Edit posts in my favorit text editor with favorite markup
* NO PHP
* Syntax hightlight out of the box

<!--more-->

### Migration from WordPress

Two main migration points was:

* Posts that was migrated with [sereral lines of ruby code](http://google.com/search?q=wordpress jekyll migrate)
* Comments that imported to [disque](http://wordpress.org/extend/plugins/disqus-comment-system/) as it's jekyll is static site engine so the comments should be hosted somewhere else

One problem I am currently have is "post preview" feature that is currently unsupported in jekyll.
My current approach for this looks like this:

    post.content | replace_first:'<!--more-->','<!--' | append:'-->' 

### Result

About 12 hours of work to transfer 30 posts and their comments. 
Reworked site design to be more clean.
