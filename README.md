Docker Shopware Image
========================

This is just a simple shopware php container with needed php extensions for php 7.0 (not 7.1 cause of missing ioncube extension).

EXAMPLE:
-------

```
version: '2'
services:
    server:
        image: webdevops/apache:latest
        volumes_from:
            - php
        ports:
            - 80:80
        links:
            - php
        environment:
            WEB_DOCUMENT_ROOT: /var/www/html
            WEB_PHP_SOCKET: php:9000
    php:
        image: migoapps/docker-shopware:1.1.0
        volumes:
            - ./:/var/www/html
        links:
            - db
    db:
        image: mysql:latest
        ports:
            - 3306:3306
        environment:
            MYSQL_ROOT_PASSWORD: secret
            MYSQL_DATABASE: shopware
            MYSQL_USER: db
            MYSQL_PASSWORD: db
```