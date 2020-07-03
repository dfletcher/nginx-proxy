
# Launcher for nginx-proxy

Use docker-compose to launch a network named "public_network" that will route traffic to containers by VIRTUAL_HOST name.

Requires docker-compose 3.5+

This project is a minimum configuration launcher for the excellent combination of https://hub.docker.com/r/jwilder/nginx-proxy/ and https://hub.docker.com/r/jrcs/letsencrypt-nginx-proxy-companion/

You can add nginx configuration options to `proxy.conf`.

## Usage

    $ git clone https://github.com/dfletcher/nginx-proxy
    $ cd nginx-proxy
    $ docker-compose up -d

## Project docker-compose.yml

A docker-compose.yml file using `nginx-proxy` might look something like this:

    version: '3.5'

    services:

        web:
            build:
                context: .
            networks:
                - public_network
                - private_network
            volumes:
                - ./:/app
            environment:
                - VIRTUAL_HOST=website.com
                - LETSENCRYPT_HOST=website.com

        mysqldb:
            image: mariadb
            networks:
                - private_network
            command: --default-authentication-plugin=mysql_native_password
            restart: always

    networks:
        public_network:
            external:
                name: public_network
        private_network:
            driver: bridge

For local development, invent a domain name that does not exist and use that value for VIRTUAL_HOST. Also put the newly invented domain name in your local system hosts file.
