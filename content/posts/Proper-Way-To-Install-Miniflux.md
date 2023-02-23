---
title: "Proper Way To Install Miniflux RSS Reader on Ubuntu 22"
date: 2023-02-21T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: ["rss"]
author: "Nijat"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: true
draft: false
hidemeta: false
comments: false
description: "How I Install Miniflux RSS reader without docker and docker-compose"
# canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "/img/miniflux.png" # image path/url
    alt: "Miniflux" # alt text
    caption: "Miniflux" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/njts/blogoes/blob/main/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---
### What is Miniflux?
[Miniflux](https://miniflux.app) is my favorite RSS reader. I enjoy using it. Recently, I attempted to install the latest miniflux reader without Docker and encountered some difficulties. Installation with Docker is straightforward, but it may be necessary to install without Docker in some cases. When I looked for resources to help me solve the problems I encountered during the installation, I found no proper online installation guide. As a result, I decided to create one. So here is it. Easy, simple Miniflux installation guide

### Before start installing the app, update the host
```
sudo apt update && sudo apt upgrade -y
```
### Add the miniflux repo
```
echo "deb [trusted=yes] https://repo.miniflux.app/apt/ /" | sudo tee /etc/apt/sources.list.d/miniflux.list > /dev/null
sudo apt update
```
### Install miniflux and other necessary components
```
sudo apt install miniflux postgresql libpq5 postgresql postgresql-client postgresql-client-common postgresql-contrib
```
### Create a database for miniflux
```
sudo -u postgres psql
```
```
create database miniflux;
```
```
create user miniflux with encrypted password 'miniflux';
grant all privileges on database miniflux to miniflux;
alter user miniflux with superuser;
\q
```
### Edit miniflux config
```
nano /etc/miniflux.conf
```
```
# /etc/miniflux.conf
RUN_MIGRATIONS=1
DATABASE_URL=user=miniflux password=miniflux dbname=miniflux sslmode=disable
LISTEN_ADDR=/run/miniflux/miniflux.sock
```
SQL migration and adding an admin user
```
miniflux -c /etc/miniflux.conf -migrate && miniflux -c /etc/miniflux.conf -create-admin
```
### Run the app
```
miniflux -c /etc/miniflux.conf
```
Press `Crtl+Z` to go back

### Install nginx and certbot
```
sudo apt update
sudo apt install nginx certbot python3-certbot-nginx -y
```
```
sudo nano /etc/nginx/sites-available/miniflux
```
### Nginx config must be like this
```
# Change miniflux.example.com with your domain
server {
    server_name     miniflux.example.com;
    listen          80;

    location / {
        proxy_pass  http://unix:/run/miniflux/miniflux.sock;
        proxy_redirect off;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```
### Enable the config
```
sudo ln -s ../sites-available/miniflux /etc/nginx/sites-enabled/miniflux
sudo certbot --non-interactive --redirect --agree-tos --nginx -d miniflux.example.com -m me@example.com
```
### Configure systemd service 
```
sudo nano /etc/systemd/system/miniflux.service
```
```
[Unit]
Description=Miniflux
After=syslog.target network.target

[Service]
Type=simple
User=miniflux
ExecStart=/usr/bin/miniflux -c /etc/miniflux.conf
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```
Reload the Systemd daemon
```
sudo systemctl daemon-reload
```
Start the service and enable to start on host boot
```
sudo systemctl start miniflux && sudo systemctl enable miniflux
```
Check the service status
```
sudo systemctl status miniflux
```
![meson-dash](/img/miniflux-systemd.png)

## Ta-Da!! Your miniflux instance is ready!