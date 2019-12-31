---
title: low cost sensor networks
summary: Real-time sensor networks and dashboards for monitoring environmental data.
tags: 
  - Data science
  - Water
  - Web
date: "2019-12-30T00:00:00Z"

# Optional external URL for project (replaces project detail page).
#external_link: "http://calwaterquality.com"

image:
  caption: 
  focal_point: Smart
  preview_only: true

links:
- icon: github
  icon_pack: fab
  name: Github
  url: https://github.com/richpauloo/cosumnes_shiny
- icon: ''
  icon_pack: ''
  name: Paper
  url: http://www.richpauloo.com/publication/lcsn/

#url_code: ""
#url_pdf: ""
#url_slides: ""
#url_video: ""



# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""


---

I have built a number of custom solutions for automated, real-time streaming of environmental data from sensor-networks deployed in the field, directly to the web.  

{{< figure library="true" src="lcsn1.png" >}} 

{{< figure library="true" src="lcsn2.png" title="An older version of a groundwater observatory, [which you can interact with here](http://ucwater.org/gw_obs/)." >}}  


{{% alert note %}}
I'm currently working on a [new lightweight, scalable groundwater observatory dashboard](http://richpauloo.com/gwo/) extensible enough to be easily applied to any [low cost sensor network]({{< ref "/publication/lcsn/index.md" >}}), written primarily in `R`, `JS`, `HTML/CSS`, and deployed on `AWS` (example below):  
{{% /alert %}}

{{< figure library="true" src="watergrid_mockup.png" title="A groundwater observatory demo, [which you can interact with here](https://richpauloo.github.io/gwo/)." lightbox="false" >}}  

Although I emphasize groundwater monitoring to support implementation of [California's Sustainable Groundwater Management Act](https://water.ca.gov/Programs/Groundwater-Management/SGMA-Groundwater-Management), this tool is customizable and general enough to be applied to real-time data from any sensor.  

{{% alert note %}}
For consulting inquiries, please [contact me]({{< ref "/#contact" >}}).
{{% /alert %}}
