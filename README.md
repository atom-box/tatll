# Content and server for my blog

## This Blog

Tattl.me is my very modest blogging effort. It contains a few notes about web development. This blog is at [https://tatll.me](https://tatll.me)

## Contact me

I am at [Little Furnace](http://littlefurnace.com) 

## Generated with Eleventy

This is an <a href="https://www.11ty.dev/">Eleventy project</a> created from the <a href="https://github.com/11ty/eleventy-base-blog"><code>eleventy-base-blog</code> repo</a> Eleventy allows you to write in markdown and then generate a JAMstack static site.  It's very secure and lightweight. I find it a little incovenient for adding images.  
   
 
## How to add content
Just copy any markdown file from `/posts` and then re-build the site by typing `npx eleventy`  

## Lots of folder here, but where are the pages
The static pages are generated and end up in the directory ___site__ .  That directory is where Apache web server is serving from. And the structure there is exactly the hierarchical path structure accessible in the client browser.

## How to view locally
During editing you can see the current built version of your site locally by just opening `/_site/index.html` in a browser. You don't need to point Apache at it or start a Node anything. It's a static site, just a bunch of linked files: there's no reason to have a server running.
