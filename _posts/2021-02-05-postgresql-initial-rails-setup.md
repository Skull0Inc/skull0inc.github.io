---
layout: post
title: "Postgresql"
description: "Quick Rails integration"
categories: [Database, Postgresql, Rails]
tags: [database, postgresql, rails]
---

### Quick Postgresql Rails Initial DB Setup (DEVELOPMENT MODE)

#### 1. Logging in
~~~
$ sudo -u postgres psql
~~~

#### 2. Create User 
~~~
=# create user rails with password 'password'; 
~~~

Production passwords are created another way using application secrets.

#### 3. Assign User Privileges 
~~~
=# alter role rails superuser createrole createdb replication;
~~~

#### 4. Create Database With Assigned User
~~~
=# create database <database_name> owner rails;
~~~

#### 5. Rails onfig
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
