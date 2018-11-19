---
layout: post
title: "Adding custom fonts (Icomoon) to Jekyll"
description: "Adding Icomoon to Jekyll"
categories: [jekyll]
tags: [jekyll,icons,fonts,icomoon]
---

## Description
While beginning this **Jekyll** blog, I came across the desire to add custom icons to the set, but wasn't sure exactly how to. Initially I starte
with [ Font-Awesome ](https://fontawesome.com) which could be integrated through the use of a Gem:[jekyll-font-awesome-sass](https://github.com/drewish/jekyll-font-awesome-sass), however realized I only needed a custom subset of icons and decided to go with [Icomoon](https://icomoon.io) instead. 

Assuming you already know the awesomeness that Icomoon is; I'll imagine you already know how to select and download custom font sets, and if not go learn how to do so now!


### The Process

1. Download the custom set of icons (**icomoon.zip**) and extract to some relative location.
2. Copy '<b>icomoon/fonts/*</b>' files to '<b>\<your-project-name\>/assets/fonts/*</b>'. 
3. Move '<b>icomoon/style.css</b>' to '<b>\<your-project-name\>/_sass/custom-icons.scss</b>'; note the **.scss** extension.
4. Open the '<b>_sass/custom-icons.scss</b>' file.
5. Change **all the url paths** by prepending `../font` before the `font/icomoon.*`.
#### Example
   * url('fonts/icomoon.eot?fscaxe');
   * url('`../`fonts/icomoon.eot?fscaxe');

6. For **my** particular case I have <b>both</b> `simple-texture-{blog,home}.scss` within the `_sass` folder.
7. Add the relative **@import 'custom-icons';** to the main .scss file(s) to include the icons.
8. Remember the semi-colon at end of the <b>@import 'custom-icons';</b>  statement.



##### End Notes

---
In summary, all that we are really doing here is: 
* choosing the fonts we need from Icomoon App
* copying the relevant files over into the correct places( the icon-font files and they css styling )
* updating the font <b>src: url('correct-font-path')</b> paths.
* adding <b>@import 'custom-icons';</b>to the main scss file(s).

Also, at the end of the src: url('\<some path\><b>?\*\*\*\*\*\*</b>') path from the original <b>icomoon/style.css</b> file there are extra characters like :
url('../fonts/icomoon.eot**?fscaxe**'); I am not quite sure what they are, but they don't have an affect if not changed when updating the src url.
They are probably some cache-busting technique so the browser doesn't load old icon files from a cached copy.


