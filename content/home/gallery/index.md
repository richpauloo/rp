+++
# A pictures gallery section created with the Blank widget.
# Any elements can be added in the body: https://sourcethemes.com/academic/docs/writing-markdown-latex/
# Add more sections by duplicating this file and customizing to your requirements.

widget = "blank"  # See https://sourcethemes.com/academic/docs/page-builder/
headless = true  # This file represents a page section.
active = true  # Activate this widget? true/false
weight = 80  # Order that this section will appear.

title = ""
subtitle = ""

[design]
  # Choose how many columns the section has. Valid values: 1 or 2.
  columns = "1"

[design.background]
  # Apply a background color, gradient, or image.
  #   Uncomment (by removing `#`) an option to apply it.
  #   Choose a light or dark text color by setting `text_color_light`.
  #   Any HTML color name or Hex value is valid.

  # Background color.
  # color = "navy"
  
  # Background gradient.
  # gradient_start = "DarkGreen"
  # gradient_end = "ForestGreen"
  
  # Background image.
  # image = "image.jpg"  # Name of image in `static/img/`.
  # image_darken = 0.6  # Darken the image? Range 0-1 where 0 is transparent and 1 is opaque.
  # image_size = "cover"  #  Options are `cover` (default), `contain`, or `actual` size.
  # image_position = "center"  # Options include `left`, `center` (default), or `right`.
  # image_parallax = true  # Use a fun parallax-like fixed background effect? true/false
  
  # Text color (true=light or false=dark).
  text_color_light = true

[design.spacing]
  # Customize the section spacing. Order is top, right, bottom, left.
  padding = ["20px", "0", "20px", "0"]

[advanced] 
 # Custom CSS. 
 #css_style = ""
 
 # CSS class.
 #css_class = ""

[[gallery_item]]
  album = "gallery"
  image = "climb_wide.png"
  caption = "Exploring the Sierra Nevada on the West Ridge of Mt. Conness, summer 2019."
  
[[gallery_item]]
  album = "gallery"
  image = "speak.jpg"
  caption = "Presenting at the 2019 California Water Data Summit."

[[gallery_item]]
  album = "gallery"
  image = "temple.jpg"
  caption = "Atop Temple Crag (2017)."

[[gallery_item]]
  album = "gallery"
  image = "agu.jpg"
  caption = "Presenting at the AGU 2019 Fall meeting, where I had the honor of winning the Outstanding Student Presentation Award (OPSA)!"

[[gallery_item]]
  album = "gallery"
  image = "eichorn.jpg"
  caption = "Atop Eichorn's pinnacle (2017)."

[[gallery_item]]
  album = "gallery"
  image = "geochem.jpg"
  caption = "Aqueous geochemistry art."

[[gallery_item]]
  album = "gallery"
  image = "hangar.jpg"
  caption = "A space shuttle fits inside this hangar!"

[[gallery_item]]
  album = "gallery"
  image = "lauterbrunnen.jpg"
  caption = "Hiking in the Alps near Lauterbrunnen, Switzerland (2018)."

[[gallery_item]]
  album = "gallery"
  image = "snow.jpg"
  caption = "Goofing off near Tahoe in winter."

  
+++

<center>{{< gallery >}}</center>
