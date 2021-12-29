# Docker Compose Cheatsheet

## Sample `docker-compose.yml` file

Here is a sample `docker-compose.yml` file:

```yaml
version: '3.9'
services:

  mysqldb:
    image: mysql:5.7
    ports:
      - 3306:3306
    volumes:
    - ./docker/mysql/data:/var/lib/mysql
    - ./docker/mysql/my.cnf:/etc/mysql/my.cnf
    - ./docker/mysql/run:/var/run/mysqld
    environment:
      MYSQL_ROOT_PASSWORD: rootpassword
      MYSQL_DATABASE: my_db
      MYSQL_USER: my
      MYSQL_PASSWORD: mypassword

  redis:
    image: "redis:alpine"
    ports:
      - 6379:6379

  web:
    build: .
    stdin_open: true
    tty: true
    environment:
      DJANGO_SETTINGS_MODULE: my_project.settings.dev_docker
    ports:
      - 8000:8000
    volumes:
      - ./:/src
    command: python manage.py runserver 0.0.0.0:8000
    depends_on:
      - mysqldb
      - redis
    links:
      - mysqldb:mysqldb
      - redis:redis
      %
```

## Build a Docker Compose Setup

The following command fetches all the dependency images and builds the image, but doesn't run the image as a container.

```
docker-compose build
```

## Launch a Docker Compose Setup

The following command builds the image, if it is not already built, and launches the container:

```
docker-compose up
```

## Shutdown Docker Compose Setup

The following command shuts down all the running containers setup with `docker-compose up`.

```
docker-compose down
```

## Check State of Docker Compose Containers

The following command shows the state of all the containers managed by docker compose.

```
docker-compose ps
```

## Run a Command on a Running Container in the Docker Compose Setup

The following command runs a given command (let's say `ls -lah` in a container that is running
that is managed by docker compose)

```
docker-compose run web sh -c "ls -lah"
```

Let's break down this command:

* `docker-compose run` - runs the command in a container managed by docker-compose.
* `web` - the name of the container that we want to run the command in.
* `sh -c "ls -lah"` - invokes `sh` shell, and runs the `ls -lah` command inside it.

