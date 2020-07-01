---
title: Embed plotly graphs in Hugo markdown
author: Rich
date: '2020-06-15'
slug: embed-ploty
categories: []
tags: []
subtitle: ''
summary: 'Embed interactive graphics made with plotly into Hugo pages with custom shortcodes.'
authors: []
#lastmod: '2019-12-29T09:47:33-08:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

I recently wanted to embed a plotly graph into a Hugo markdown file and found the process complicated and fraught with errors. The successful piece is [here](https://richpauloo.com/talk/2020-exit-seminar/), and below is another example:

{{<load-plotly>}}
{{<plotly json="" height="400px">}}

I use `R` and [`blogdown`](https://sourcethemes.com/academic/docs/install/#install-with-rstudio) to build this site. Including interactive html widgets in a blog post is very straightforward with a `.Rmd` file. However, not everyone that uses Hugo and plotly uses `.Rmd` files, even in my case, I needed to embed a plotly graph into a `.md` file. 

Hugo doesn't parse HTML, so you can't just include raw HTML into a `.md` file. The workaround, which ends up being much cleaner, is to write *shortcodes*, which are like functions that you can call from within a `.md` file using 

```
{{<shortcode-name>}}
```


Hugo looks for shortcodes in two places: 

* `/layouts/shortcodes/`
* `/themes/[theme-name]/layouts/shortcodes/`

But Netlify will only look for shortcodes in `/layouts/shortcodes/`! If the shortcodes are placed in `/themes/[theme-name]/layouts/shortcodes/`, you might get an Netlify error like this: 

```
Error: Error building site: "/opt/build/repo/content/talk/2020-exit-seminar/index.md:71:1": failed to extract shortcode: template for shortcode "load-plotly" not found
```

his means that Hugo is looking for the shortcode `"load-plotly"` specified in `"/opt/build/repo/content/talk/2020-exit-seminar/index.md:71:1"`, but can't find it. The solution is to create a `/layouts/shortcodes` in the root directory, and place the shortcodes in there. So you'll have `/layouts/shortcodes/load-plotly.html` and `/layouts/shortcodes/plot.html`. 



Here are some resources I found helpful in writing this short summary:

1. [Embedding plotly into Hugo with shortcodes](https://ig248.gitlab.io/post/2018-11-05-plotly-sample/)
2. [Hugo errors explained](https://kodify.net/hugo/errors/shortcode-not-found/#cause-4-hugos-shortcode-file-in-the-wrong-theme-folder)

