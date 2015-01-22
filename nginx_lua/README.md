## Nginx_lua Dockerfile


This repository contains **Dockerfile** of [Nginx](http://nginx.org/) [lua-nginx-module](https://github.com/chaoslawful/lua-nginx-module.git) [echo_nginx_moudle](https://github.com/agentzh/echo-nginx-module.git) [ngx_devel_kit](https://github.com/simpl/ngx_devel_kit.git)  for [Docker](https://www.docker.com/)'s published to the public [Docker Hub Registry](https://registry.hub.docker.com/).


### Base Docker Image

* [ubuntu:14.10](http://dockerfile.github.io/#/ubuntu)


### Installation

1. Install [Docker](https://www.docker.com/).

2. Download [automated build](https://registry.hub.docker.com/u/dockerfile/nginx/) from public [Docker Hub Registry](https://registry.hub.docker.com/): `docker pull ubuntu:14.10`

   (alternatively, you can build an image from rake: `rake docker:build`)


### Usage

    docker run -d -p 80:80 nginx_lua/v1
    (alternatively, you can build an image from rake: `rake "docker:run[port]"`)

#### Attach persistent/shared directories

    docker run -d -p 80:80 -v <sites-enabled-dir>:/etc/nginx/sites-enabled -v <certs-dir>:/etc/nginx/certs -v <log-dir>:/var/log/nginx -v <html-dir>:/var/www/html nginx_lua/v1.0

After few seconds, open `http://<host>/lua?query=xoxo` to see the welcome page.
