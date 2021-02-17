---
layout: post
title: "WebpackER: Dealing with Image assets"
description: "Basic configuration for Images"
categories: [Rails, Webpacker]
tags: [frontend]
---

### Webpacker: Dealing with Image assets

Almost every time I approach Webpacker there seems to be some kind of new neuance of something or another I may have seemed to have overlooked, or underlooked for that matter.
Therfore every time I encounter any issues I will have them documented for future reference (if its even still valid then). 

#### The Structure 
```
app/javascript
│ 
├── components
│   └── Vue.js
│ 
├── css
│   ├── application.css
│   │ 
├── images
│   ├── devise.jpg
│   ├── bulma.jpg
│   └── logo.jpg
└── packs
    └── application.js
```

Just place the **`app/javascript/images/`** folder location immediately inside the **`app/javascript/`** folder.
From there place any assosciated images in there. 


#### The Reference

In order for Webpacker to gain access and *know* how to find the images (which it does not by default), they will have to be referenced. To do this, we will make reference to the
file to add an entry point for the images.

>`app/javascript/packs/application.js` 
```javascript
import Rails from "@rails/ujs"
import Turbolinks from "turbolinks"
import * as ActiveStorage from "@rails/activestorage"
import "channels"

// This will load all ../images/* one level up from here.
const images = require.context('../images', true) 
```

Now that the reference has been added in the javascript file, make sure to restart `./bin/webpack-dev-server` in the rails *root* folder.

Next is to actuallly reference and use the image in a *view* file. **note** images are referenced by pre-pending **`media/images/`** to the path name. Therefore an image would be referenced as:
`media/images/logo.jpg`

#### In View

So in my view I could have something like:
> app/views/layouts/_nav.html.haml

~~~haml
-# in Haml
%img { src: "#{asset_pack_path 'media/images/logo.jpg'}" }/
~~~


> app/views/layouts/_nav.html.erb

~~~erb
<!-- in erb -->
<img src="<%= asset_pack_path 'media/images/logo.jpg' %>" />
~~~

That's it for now for this really quick reference. In the future I will add accessing images from `.css` and `.sass `
#### In Sass or CSS

