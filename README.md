# Docker image for php 5.2 legacy projects

This docker image is intended to work as a replacement for old legacy projects, running on old server.

Features:
* Features included from the [original repository](https://github.com/kuborgh/docker-php-5.2):
    * Based on Ubuntu 12.04
    * Apache MPM Prefork
    * PHP 5.2.17 as apache mod
    * Zend Optimizer
* Features added by [Demin](https://github.com/deminy/docker-php-5.2)
    * Enable PHP on the default site.
    * Allow [short open tag](http://php.net/manual/en/ini.core.php#ini.short-open-tag).
    * Various updates and fixes.
* Features added by Moollllee
    * Ioncube Loader
    * upload_max_filesize = 32M

# Sample Docker compose file

```yaml
version: '3'

services:
  app:
    image: deminy/php-5.2
    ports:
      - "80:80"
    volumes:
      - ~/projects/example.com:/project
```

# Creating your own Docker Image for Docker Hub
I use this Docker Image in Plesk for an older project the client wants to keep online.
1. Clone Repo
2. Edit Dockerfile, php.ini,...
3. run Docker build & push to docker hub
```sh
$ cd docker-php-5.2-master
$ docker build -t your-docker-hub-repo/php-5.2-ioncube .
$ docker push your-docker-hub-repo/php-5.2-ioncube
```
   Maybe login before if not already
```sh
$ docker login -u example-docker-username
```
4. Install Docker Image in Plesk with Auto-Port-Mapping
5. ...
