---
layout: post
title: "Managing Simple Texture(this) Jekyll Blog"
description: "Managing Simple Texture(this) Jekyll Blog"
categories: [Jekyll, Blog]
tags: [blog,theme]
---

### Updating the Blog (pushing from localhost to gh-pages)

At some stage I added the blog - I believe through forking and cloning the original theme and then begun editing, customizing a few things along with mainly adding my own posts. It was saved using Git, pushed to GitHub and GitHub Pages along the special branch `gh-pages`.

In GitHub there is the option to choose which branch to use, whether **'master'** or **'gh-pages'**. In our case we make sure that **'gh-pages'** is selected. When we now commit and push the **'gh-pages'** branch, the live site is updated.

### Important Sections (Layout & Data) for Customizing

Edit stuff in these sections to change layouts 

The `_layouts/` folder is pretty much self-explanitory in terms of the naming of things within, however there are a few things that may not be so obvious, especially being new to Jekyll.

* *_layouts/home.html* >> The entrance that says 'MindJective', 'Blog'. Add other sections here.
* *_layouts/blog.html* >> This is the general **template** used for anything associated with 'Blog'.
* *_layouts/page.html* >> This is the index page for listing all posts, it uses the 'Blog' template.
* *_layouts/post.html* >> This is the detail view for any selected post. It uses the 'Blog' template
* *_layouts/redirect.html* >> Not quite sure at the moment how this redirect works.. . . 

The above secions make references to the `_data/i18n.yml` file which is accessed through the liquid templating syntax. Liquid won't really be discussed here however its specific syntax reference can be found [ here ](https://shopify.github.io/liquid/). This file is mainly for supporting translation of different languages; however seems to be used as a global area for storing global settings for common areas of the site.

Generally the user of this blog is mainly interested in the `_posts` folder where new posts are added or the `_drafts` where unfinished posts are kept.

