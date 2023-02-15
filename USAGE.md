# How to use this image

## Docker

The basic pattern for starting a GovCMS proof-of-concept instance is:

```bash
docker run --name govcms-d10-test -p 8080:80 -d govcmspoc/govcms:drupal10
```

Then, access it via http://localhost:8080 or http://host-ip:8080 in a browser.

There are multiple database types supported by this image, most easily used via Docker networks. In the default configuration, SQLite can be used to avoid a second container and write to flat-files.

* MySQL https://hub.docker.com/_/mysql/
* PostgreSQL https://hub.docker.com/_/postgres
* MariaDB https://hub.docker.com/_/mariadb

## Docker compose

```docker
services:
  ##################################################
  # govcms: The GovCMS drupal 10 site used by local
  ##################################################
  drupal:
    image: govcmspoc/govcms:drupal10
    ports:
      - 8080:80
    volumes:
      - ./modules/govcms:/app/web/modules/develop
      - ./themes/govcms:/app/web/themes/develop
      # this takes advantage of the feature in Docker that a new anonymous
      # volume (which is what we're creating here) will be initialized with the
      # existing content of the image at the same location
      - /var/www/html/sites
    restart: always

  ##################################################
  # mariadb: The database used by local
  ##################################################
  mariadb:
    image: mariadb
    environment:
      MARIADB_ROOT_PASSWORD: root
      MARIADB_DATABASE: drupal
      MARIADB_USER: drupal
      MARIADB_PASSWORD: drupal
    volumes:
      - ./database:/var/lib/mysql
```

## Drupal tools

### Drupal Rector

https://github.com/palantirnet/drupal-rector

Analyze your code with Rector and review suggested changes.

```bash
ahoy rector process web/modules/minisite --dry-run
```

Apply suggested changes

```bash
ahoy rector process web/modules/minisite
```

### PHPUnit

```bash
ahoy phpunit -c web/core web/modules/minisite
```

### Drupal Check

https://github.com/mglaman/drupal-check

```bash
ahoy drupal-check web/modules/minisite
```
