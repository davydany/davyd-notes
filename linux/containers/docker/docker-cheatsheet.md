# Docker Cheatsheet

## Simple Dockerfile

Here is a simple Dockerfile that I used to have a test app up and running:

```Dockerfile
FROM python:3.11.0a3-alpine3.15
LABEL author "David Daniel <davydany@aeroxis.com>"

EXPOSE 8888/tcp

RUN mkdir -p /mnt/s3data
RUN mkdir -p /data
RUN ln -s /mnt/s3data /data/input
WORKDIR /data/input
CMD python -m http.server 8888
```

## Build a Docker Container

Assuming the name of the container is `davydany/my-docker-container`, and your
current directory has a `Dockerfile`, set it up like so:

`docker build -t davydany/my-docker-container .`

This builds the docker image and stores the built image in your local file system.

## Push a Docker Container to Remote Repository

Now that your docker container has been built locally, we want to deploy the image 
to a remote docker image repository. Let's assume the hostname is `my-docker-hub.com`
and the organization/username is `davydany`, and the image is `my-docker-container`,
then run this command:

```
docker push my-docker-hub.com/davydany/my-docker-container
```

## Run a Built Image

Now that you have a built image locally, let's run it by running the following command:

```
docker run <image-name>
```

If you want this image to run in the background (daemonized), run:

```
docker run -d <image-name>
```

# Attach to a Running Container

To attach to a running container, run `docker ps` to get the container ID of the container you want to
attach to, and then run:

```
docker exec -it <CONTAINER_ID> /bin/sh
```

This will open up a shell instance for you 