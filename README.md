# wordpress-phpunit

WordPress with PHPunit in one Docker unit in such a way that you can use it for running tests with the WordPress database with Github actions and docker-compose.

![Docker](https://github.com/Shelob9/wordpress-phpunit/workflows/Docker/badge.svg)

> [Avaible via Github docker package registry](https://github.com/Shelob9/wordpress-phpunit/packages/308041)

## Usage

Pressuming you have logged into Github's Docker registry, which by default, you are not. You can pull this image like this:

```sh
docker pull docker.pkg.github.com/shelob9/wordpress-phpunit/wordpress-phpunit:0.0.1
```

### docker-compose

This example might work, not sure. Good luck.

```yml
version: "3.7"

services:
  wordpress:
    image: wordpress
    ports:
      - 8111:80
    environment:
      WORDPRESS_DB_PASSWORD: example
      WORDPRESS_DEBUG: 1
      WORDPRESSS_DEBUG_LOG: example
      ABSPATH: /usr/src/wordpress/
    volumes:
      - wordpress:/var/www/html
      - ./:/var/www/html/wp-content/plugins/plugin-name
  cli:
    image: wordpress:cli
    volumes:
      - wordpress:/var/www/html
      - ./:/var/www/html/wp-content/plugins/plugin-name
    environment:
      WORDPRESS_DB_PASSWORD: example
      ABSPATH: /usr/src/wordpress/
  wordpress_phpunit:
    build:
      context: ./
      dockerfile: WPTESTS
    environment:
      PHPUNIT_DB_HOST: mysql
    volumes:
      - .:/app
      - testsuite:/tmp
  mysql:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
      MYSQL_DATABASE: wordpress_test
  composer:
    image: composer
    volumes:
      - .:/app

volumes:
  wordpress:
  testsuite:
```

### Setting Up Docker

You must be logged in to Github docker registry to pull this image. Sorry, but you have to.

Short version:

- Create a token
  - https://github.com/settings/tokens/new
- `docker login https://docker.pkg.github.com -u user_name --password actual_token`
- Provide password for user sheluser_nameob9.

#### Infomations

- https://docs.github.com/en/packages/using-github-packages-with-your-projects-ecosystem/configuring-docker-for-use-with-github-packages#authenticating-to-github-packages
- https://github.community/t/error-response-from-daemon-unauthorized-when-im-trying-to-pull-public-image-from-gpr/2614/7
