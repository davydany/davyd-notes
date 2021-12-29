# Docker Cheatsheet

## Build a Docker Container

Assuming the name of the container is `davydany/my-docker-container`, and your
current directory has a `Dockerfile`, set it up like so:

`docker build -t davydany/my-docker-container .`

This builds the docker image and stores the built image in your local file system.

## Push a Docker Container to Remote Repository

Now that your docker container has been 

```
docker push gitlab-registry.gs.mil/enterprise_knowledge_management/idt
```