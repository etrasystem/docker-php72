# PHP 7.2 Apache

# How to use this image.

## With Command Line

For PHP projects run through the command line interface (CLI), you can do the following.

### build
    docker build -t etrasystem/php72:1.1 .

### Create a `Dockerfile` in your PHP project

    FROM etrasystem/php72:1.1
    COPY . /usr/src/myapp
    WORKDIR /usr/src/myapp
    CMD [ "php", "./your-script.php" ]

Then, run the commands to build and run the Docker image:

    docker build -t my-php-app .
    docker run -it --rm --name my-running-app my-php-app

### Run a single PHP script

For many simple, single file projects, you may find it inconvenient to write a complete `Dockerfile`. In such cases, you can run a PHP script by using the PHP Docker image directly:

    docker run -it --rm --name my-running-script -v "$PWD":/usr/src/myapp -w /usr/src/myapp etrasystem/php:5.3-apache php your-script.php

### Installing modules

To install additional modules use a `Dockerfile` like this:

``` Dockerfile
FROM etrasystem/php:5.3-apache

# Installs curl
RUN docker-php-ext-install curl
```

Then build the image:

``` bash
$ docker build -t my-php .
```

### Without a `Dockerfile`

If you don't want to include a `Dockerfile` in your project, it is sufficient to do the following:

    docker run -it --rm --name my-php-app -v "$PWD":/var/www/html etrasystem/php:5.3-apache

## Credits

A big credit to [helderco](https://github.com/helderco/docker-php-5.3) for the `fpm` version
of this image.

# License

View [license information](http://php.net/license/) for the software contained in this image.


