---
layout: post
title: "Adding HTTPS to Rails-Nginx App"
description: "Adding HTTPS/ssl to Rails-Nginx config"
categories: [Rails, Nginx]
tags: [rails, ssl, nginx, https]
---


# Adding HTTPS to Rails-Nginx App (LetsEncrypt)

This process can be broken down into (3) main sections:
1. Configuring Rails for ssl
2. Installing and setting up LetsEncrypt
3. Configuring Nginx to allow and redirect to HTTPS

### 1. Configure Rails for HTTPS

 The main(only) file to focus on is >>  `/config/environments/production.rb`

~~~ ruby
#Force all access to the app over SSL, use Strict-Transport-Security, and use secure cookies.
config.force_ssl = true
~~~ 

### 2. Setting up LetsEncrypt

in `/home/<your_username>/` directory, or some other directory of choice, do the following in terminal:
~~~ bash
git clone https://github.com/letsencrypt/letsencrypt
cd ./letsencrypt && ./letsencrypt-auto
# Do a dry run TEST
sudo ./certbot-auto certonly --standalone -d <domain_name>.com -d www.<domain_name>.com --dry-run
# Once everything with dry run checks out then do full run
# Note: In some instances Nginx may need to be halted with: sudo service nginx stop to get access to port 80
sudo ./certbot-auto certonly --standalone -d <domain_name>.com -d www.<domain_name>.com
# Enter crontab settings
sudo crontab -e 
# Make new setting to renew certificates, in this case: (Every Saturday at 9:05 a.m)
05 9 * * * cd /etc/letsencrypt/ && ./certbot-auto renew && /etc/init.d/nginx reload
~~~

Note: the above *most likely will* install its own config stuff within an existing nginx config file. All of the stuff added is necessary for it 
to work, however can be altered slightly as seen below.

### 3. Configuring Nginx config file (remote server)

This can involve quite a few steps, however I've made a gist file which can be copied from [default-rails-ssl-nginx-config](https://gist.github.com/Skull0Inc/d403bbc51a7a8b43b625cee158d6674a/raw/default-rails-ssl-nginx-config)

To set this file up navigate to the `/etc/nginx/sites-available` folder and run:
~~~ bash
# Download the gist file, using the below command or just get access to the above linked info into a file somehow
wget https://gist.github.com/Skull0Inc/d403bbc51a7a8b43b625cee158d6674a/raw/default-rails-ssl-nginx-config

# After file downloads move it to a more preferred <your_app_name> (the name of your new Rails upstream)
mv default-rails-ssl-nginx-config <your_app_name>

# IMPORTANT: Make sure to EDIT and replace all occurances of <app_name> and <domain_name> with the correct info.
vim <your_app_name>
..
..
..
# Make appropriate changes
~~~
Next we need to create a symbolic link in `sites-enabled` that points to the newly created `<your_app_name>` file we just downloaded/created in `sites-available` . Do the following:
~~~ bash
# Reference ln -s {source-filename} {symbolic-filename}
# Go to /etc/nginx/sites-enabled/ and run
ln -s /etc/nginx/sites-available/<your_app_name> /etc/nginx/sites-enabled/<your_app_name>

# Restart Nginx
sudo service nginx reload
# OR start if not already running
sudo service nginx start
~~~


Notes about this setup >> At the time of setup for me there was already a set @app running for Rails and LetsEncrypt was setup **after**; therefore the order of doing things may not be exactly suited for every individual case, and not meant as a follow-blindly guide but more as a reference of steps needed.

