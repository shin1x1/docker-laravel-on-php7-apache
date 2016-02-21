# docker-laravel-on-php7-apache

Docker image for Laravel 5.1 on `php:7-apache`
[https://hub.docker.com/r/shin1x1/laravel-on-php7-apache/](https://hub.docker.com/r/shin1x1/laravel-on-php7-apache/)


## Usage

```
$ cd /path/to/laravel-application
$ docker run -v `pwd`:/var/www/html -p "8000:80" shin1x1/laravel-on-php7-apache
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 172.17.0.2. Set the 'ServerName' directive globally to suppress this message
[Mon Feb 15 14:32:23.701732 2016] [mpm_prefork:notice] [pid 1] AH00163: Apache/2.4.10 (Debian) PHP/7.0.3 configured -- resuming normal operations
[Mon Feb 15 14:32:23.702131 2016] [core:notice] [pid 1] AH00094: Command line: 'apache2 -D FOREGROUND'

$ docker run shin1x1/laravel-on-php7-apache php -v
PHP 7.0.3 (cli) (built: Feb  5 2016 18:24:39) ( NTS )
Copyright (c) 1997-2016 The PHP Group
Zend Engine v3.0.0, Copyright (c) 1998-2016 Zend Technologies
    with Zend OPcache v7.0.6-dev, Copyright (c) 1999-2016, by Zend Technologies
```

## docker-composer (with postgres)

```
$ docker-compose up -d

# application setting
$ cp .env.example .env
$ docker-compose run web php artisan key:generate
$ docker-compose run web php artisan migrate
$ docker-compose run web php artisan db:seed

# PHPUnit
$ docker-compose run web ./vendor/bin/phpunit
```

If you would like to modify PHP settings via `php.ini`. This file configured for Xdebug remote debug and some example settings.

```
; timezone
;date.timezone = Asia/Tokyo

; error reporing
;log_errors = On
;error_log = /var/log/php.log

; xdebug
xdebug.remote_enable = On
xdebug.remote_autostart= On
xdebug.remote_connect_back = On
;xdebug.remote_host = 192.168.99.1
```
