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
