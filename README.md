# gh-actions-docker-tests

## about
- caddy
- php-fpm
  - composer
  - symfony-cli


## howto
### use shell inside container
```
sudo docker exec -it gh-actions-docker-tests-php-1 sh
```

### run php coding standards fixer
```
sudo docker exec -it gh-actions-docker-tests-php-1 sh -c './vendor/bin/php-cs-fixer check --diff src'
sudo docker exec -it gh-actions-docker-tests-php-1 sh -c './vendor/bin/php-cs-fixer fix src'
```

### run phpunit tests
```
sudo docker exec -it gh-actions-docker-tests-php-1 sh -c 'php bin/phpunit --testdox'
```

### fix /srv folder permission denied
```
sudo chown -R user:group srv
```