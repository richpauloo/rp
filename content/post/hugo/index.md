---
title: Migrating from Jekyll/Github to Hugo/Netlify
author: Rich
date: '2019-12-29'
slug: migrating-to-hugo
categories: []
tags: []
subtitle: ''
summary: 'I moved my personal page from Jekyll to Hugo and recorded a few important lessons learned along the way.'
authors: []
#lastmod: '2019-12-29T09:47:33-08:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

I recently migrated my Jekyll Github Page to Hugo, deployed on Netlify. I jotted down a few things that will save me (or someone running into similar issues) time in the future.  

# Build v. deploy environments

In `netlify.toml`, make sure that `HUGO_VERSION` is set to the correct version you're building with locally. I'm building with locally with `R`, so I use:  

```r
blogdown::hugo_version()
```  
```r
[1] ‘0.61.0’
```

***

# Creating a custom theme

An annoying error that took me a while to figure out was caused by a custom theme I created in `/themes/academic/data/themes/my_custom_theme.toml`. 

```
9:31:27 AM: ERROR 2019/12/29 17:31:27 Transformation failed: SCSS processing failed: file "stdin", line 14, col 15: Invalid CSS after "$sta-primary:": expected expression (e.g. 1px, bold), was "<no value>;"
```

Moving the theme to `/data/themes/` solved the problem. For future reference, this is where user-defined themes live. 

***

# Featured posts

I also wanted to include a featured posts section for my blog, but hide the overall blog from the main page, and link to it from the featured posts page. To accomplish this, I created a `featured` widget, `/content/home/featured-posts.md`, with `page_type = "post"`. Then I added a bit of CSS after the front matter:   

```css
<style>
  div.absolute {
    position: absolute;
    width: 100%;
    bottom: 0px;
  } 
</style>
```

And a link to all the posts on the `posts` page (inactive):

```html
<div class="absolute"><a href="http://www.richpauloo.com/post/">SEE ALL POSTS >></a></div>
```

And a corresponding menu link in `menus.toml`:  

```
[[main]]
  name = "Blog"
  url = "#featured-posts"
  weight = 40
```

{{< figure library="true" src="hugo_css.png" lightbox="true">}}


***  

# Image gallery captions

According [to the docs](https://sourcethemes.com/academic/docs/writing-markdown-latex/#image-gallery) (at the time of writing), captions for gallery items in a page bundle are specified at the end of the TOML:  

```
gallery_item:
- album: <ALBUM FOLDER>
  image: <IMAGE NAME>.jpg
  caption: Write your image caption here
```

When in fact, this is the form that works:

```
[[gallery_item]]
  album = "<ALBUM FOLDER>"
  image = "<IMAGE NAME>.jpg"
  caption = "My caption."
```

[Helpful link here](https://github.com/gcushen/hugo-academic/issues/1051).
