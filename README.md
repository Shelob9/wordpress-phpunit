# wordpress-phpunit

WordPress with PHPunit in one Docker unit in such a way that you can use it for running tests with the WordPress database with Github actions and docker-compose.

- Probably could be useful now if I added docs and published to Docker hub.
- Making this useful as intended, v1:
  - https://github.com/Shelob9/wordpress-phpunit/pull/1

# Use Thing

- Type things
  - `docker-compose run --rm wordpress_phpunit bash bin/install-wp-tests.sh wordpress_test root example mysql trunk false`
