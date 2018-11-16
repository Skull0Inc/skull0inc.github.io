---
layout: post
published: true
title: "Ajax on Rails Intro"
description: "A quick demo setting up Ajax in a Rails environment"
categories: [Rails]
tags: [ajax, rails]
redirect_from:
  - /2017/05/27/
---

> Quick Overview:
  1. Open 

* Kramdown table of contents
{:toc .toc}


# Ajax Overview

What **Ajax** (Asynchronous Javascript and XML) does is to provide an asynchronous way to make **client-side HTTP requests and responses** through JavaScript. What this mainly boils down to for the user is that: there is no lengthy full-page refresh, as only the section that is requested to be updated is sent in the server response, acting similar to the "feel and speed of a single page app" - however with your friendly Rails back-end. These responses usually take place after *GET* or *POST* requests and involve some type of Javascript intervention for updating the results to the user/client.

# Ajax on Rails

There is nothing new that needs to be added to an already existing *Rails 5.0* app for Ajax to run, as it runs straight out of the box, using `jquery`, `jquery_ujs` (Unobtrusive Javascript) and just requires some **configuration** of a few things:

1. Add a `remote:true` option to the correct _form action and corresponding link methods.
2. Update the `respond_to` blocks for the `controller` CRUD methods.
3. Create new ***.js.erb** files for the above methods.
4. Add Javascript to the above files to perform the desired front-end functionality.

## Step 1

<div class="highlight-heading">app/views/tasks/_form.html.erb</div>
{% highlight eruby %}

<%= form_for @task, remote:true do |f| %>

  <div class="field">
    <%= f.label :name %>
    <%= f.text_field :name %>
    <%= f.submit %>
  </div>

<% end %>

{% endhighlight %}

Here we can see where the `remote:true` section was added to the form_for tag for the specific form making the ajax request. 
