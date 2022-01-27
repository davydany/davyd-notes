# Notes about Kubernetes

## Table of Contents

* [Kubernetes Cheat Sheet](./k8s_cheat_sheet.md)

## General Notes

### Local Development


#### Docker with Kubernetes or Minikube

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


