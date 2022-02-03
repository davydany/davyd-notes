# Minikube Cheatsheet

I use `minikube` for local development of application on Kubernetes. It is pretty straightforward and simple to use.
However, there are some commands that are best to be documented so I'm not always looking for it.

## General Notes

### Docker with Kubernetes or Minikube

I originally thought Docker with Kubernetes would be a good thing, in December 2021, when I was working on this,
but there are some weird issues with Kubernetes' shared volume mounts where it is asking the root directory `/`
to be a shared mount. It didn't make sense to me, and no matter what I did, I was not able to fix it. 

I think the best solution is to use `minikube`. It's default driver is `docker`, so it downloads Kubernetes images
and installs Kubernetes inside docker, and then you deploy into it. You can also use any of the following drivers,
but the default driver of `docker`, out of the box setup, works well: 

* `virtualbox`
* `parallels`
* `vmwarefusion`
* `hyperkit`
* `vmware`
* `docker`
* `podman`



## Starting up `minikube`

Make sure Docker Desktop is already running, and then run:

```bash
minikube start
```

## Stopping `minikube`

```bash
minikube stop
```

## Pointing Docker Daemon to `minikube`

By default, `docker` cli points to the local Docker instance on your machine when it builds images.
However, if we want Kubernetes that `minikube` is using to use images that `docker` built, we need 
the Docker Daemon to point to `minikube`.

To do this, simply run the following command before running `docker build`:

```bash
eval $(minikube -p minikube docker-env)
```

This should change your environment variables temporarily to allow for `docker build` to point to `minikube`.

If you want the docker daemon to always point to `minikube`, add `eval $(minikube -p minikube docker-env)` to your 
`~/.bashrc` or `~/.zshrc` file.

