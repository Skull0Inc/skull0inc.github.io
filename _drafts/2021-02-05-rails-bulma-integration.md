---
layout: post
title: "Rails-Bulma Integration"
description: "Adding Bulma CSS Framework to Rails 6 without Yarn"
categories: [Css,Frontend,Rails]
tags: [css, frontend, rails]
---

### Adding Bulma CSS Framework to Rails 6 Without Yarn"

#### 1. Adding Bulma to Gemfile  

~~~
# Source: https://github.com/joshuajansen/bulma-rails
gem "bulma-rails", "~> 0.9.1"
~~~

Run the `bundle` command to install.

#### 2. Import Bulma to SCSS
~~~
 *
 *= require_tree .
 *= require_self
 */

// Set custom variables here
$blue: #72d0eb;
$pink: #ffb3b3;
$pink-invert: #fff;
$family-serif: "Merriweather", "Georgia", serif;
$primary: $pink;
$primary-invert: $pink-invert;
$family-primary: $family-serif;
$primary-bg: rgb(253, 251, 236);

@import "bulma";

html, body, #app {
  height: 100%;
}

// rest of styling
~~~


#### 3. 
~~~
=# alter role rails superuser createrole createdb replication;
~~~

#### 4. 
~~~
=# create database <database_name> owner rails;
~~~

#### 5.
~~~
development:
  adapter: postgresql
  encoding: unicode
  database: projectname
  pool:
  username: rails
  password: password
~~~

In the Rails portion we sould have something like the above in the development section of `database.yml`.
