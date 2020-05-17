
# Launcher for nginx-proxy

Use docker-compose to launch a network named "public_network" that will route traffic to containers by VIRTUAL_HOST name.

Requires docker-compose 3.5+

This project is a minimum configuration launcher for the excellent combination of https://hub.docker.com/r/jwilder/nginx-proxy/ and https://hub.docker.com/r/jrcs/letsencrypt-nginx-proxy-companion/

You can add nginx configuration options to `proxy.conf`.

This launcher is used by the development environment described in the blog post [Drupal on Docker: The definitive guide](#TODOFIXME) from [MonkeysAtKeyboards](https://monkeysatkeyboards.com).


## Usage

    $ git clone https://github.com/dfletcher/nginx-proxy
    $ cd nginx-proxy
    $ docker-compose up -d
