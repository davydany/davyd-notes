# Using Docker Images with MiniKube

I wrote this documentation because I was trying to get `minikube` to use local Docker Images instead of 
going out to the internet.

## Point to MiniKube's Docker Daemon

Let's say that you have a docker image you need to build, and the desired name is `davydany/my-test-image`. 
You would build it by running `docker build . -t davydany/my-test-image`.

However, when you run `docker build`, it will add it to the local docker daemon's image repository. Instead, we want the image to go into `minikube`'s docker image repository. 

We can see what `minikube`'s settings are by running: `minikube docker-env`.

We want to configure our bash session to use minikube's Docker daemon. To do this, run the following command in your shell:

```
eval $(minikube -p minikube docker-env)
```

## Rebuild the Docker Image

Then, run `docker build -t davydany/my-test-image` to build and deploy to Minikube's docker daemon's image repository.

## Use Docker Image in Kubernetes Resource File

Now, simply run `kubectl` to apply your resource file, like this `kubectl apply -f ./path-to-yaml-file.yml`.

