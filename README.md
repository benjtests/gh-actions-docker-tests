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

### fix /srv folder permission denied
```
sudo chown -R user:group srv
```