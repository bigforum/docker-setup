# Bigforum Docker Setup


⚠️ ONLY FOR HISTORIC VALUES. DON'T DARE TO USE THIS IN ANY FORM ON A PRODUCTIVE SYSTEM. IT CONTAINS A LOT OF SECURITY ISSUES.


This repository contains a ready-to-go Docker Compose setup to run Bigforum. It spins up MySQL 5.5, Apache + PHP 5.5 and phpMyAdmin 5.1.


## Requirements

  * Docker
  * Docker Compose


## Usage

Standard build with the default settings:

> docker-compose build

The following build arguments do exist:

  * `BIGFORUM_VERSION`, e.g. `5.0.0` - any version from https://github.com/bigforum/bigforum/tags (without the `v`)
  * `BIGFORUM_PHP_VERSION`. e.g. `5.5` (default) - any PHP version from https://hub.docker.com/_/php?tab=tags which ends on `-apache`
  * `BIGFORUM_USE_CUSTOM_DATA`, `enabled` or `disabled` (default) - put PHP scripts into ./data/php and (optional) SQL dumps into ./data/mysql; uses those data respectively and ignores `BIGFORUM_VERSION` when `enabled`


For example, if you want to have a build with Bigforum `5.0.0`:

> docker-compose build --build-arg BIGFORUM_VERSION=5.0.0

Finally, start the setup with

> docker-compose up

Bigforum should be now reachable under http://localhost. You have to install it under the following URL: http://localhost/install.php.

The database settings are as follows:

```
  host: mysql
  database: bigforum
  user: root
  password: bigforum
```

phpMyAdmin should be reachable under http://localhost:8080.

To shut down everything:

> docker-compose down

Removal of the containers (probably a good idea before you rebuild with different settings):

> docker-compose rm
