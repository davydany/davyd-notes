

## Quick Cheat Sheet

kubectl Common Commands

Connecting `kubectl` to a new cluster:
* On AWS, aws eks --region <region-code> update-kubeconfig --name <cluster_name>
* All other cases: https://docs.aws.amazon.com/eks/latest/userguide/create-kubeconfig.html

Get information about the cluster
* `kubectl cluster-info`

Get information about the nodes:
* `kubectl get nodes`
* `kubectl get nodes -o wide`

Get information about the pods:
* `kubectl get pods`
* `kubectl get pods --namespace kube-system`

Get information about the pods:
* `kubectl get pods --namespace kube-system -o wide`
* `kubectl get all —all-namespaces | less `

Get All the API Resources for Kubernetes
* `kubectl api-resources | head -n 10`

You can get kubectl to explain more details about resources by running:
* `kubectl explain <resource-name> | more`
* `kubectl explain pod | more`
* `kubectl explain pod.spec | more `
* `kubectl explain pod.spec.containers | more`

Get detailed information about the master or nodes:
* # get all available nodes: kubectl get nodes
* `kubectl describe nodes <master-node>`
* `kubectl describe nodes <slave-node>`


Deployments:

Imperative Deployments - One time runs, but not a sustainable way to do things with K8s
* `kubectl create deployment nginx --image=nginx`
* `kubectl run nginx --image=nginx`
* Creates a deployment by default:
    * `kubectl create deployment hello-world —image=gcr.io/google-samples/hello-app:1.0`
    * `kubectl run hello-world --image=gcr.io/google-samples/hello-app:1.0`
* Deploy to a single pod:
    * `kubectl run hello-world-pod --image=gcr.io/google-samples/hello-app:1.0 --generator=run-pod/v1`

Declarative:
* Define our desired state in code and use a manifest to do this
* `kubectl apply -f deployment.yaml (or deployment.json)`


Start a process inside a container inside a pod
* `kubectl exec -it hello-world-pod -- /bin/sh`

Expose:
Export ports to the public world
* `kubectl expose deployment hello-world --port=80 --target-port=8080`


Another sample deployment:

`kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.4`
`kubectl expose deployment hello-minikube --type=NodePort --port=8080`

`kubectl port-forward service/hello-minikube 7080:8080`


