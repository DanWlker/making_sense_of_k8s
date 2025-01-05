## Making sense of Kubernetes

1. `Node` is a kubennetes word for computer (can be VM, physical hardware etc)

1. `pod`: A Pod is the smallest and simplest unit in the Kubernetes object model that you create or deploy. It represents one (or sometimes more) running container(s) in a cluster

### Kubectl

1. `kubectl get deployments`: create a deployment, needs `name` and `id of docker image`

    kubectl create deployment synergychat-web --image=docker.io/bootdotdev/synergychat-web:latest

1. `kubectl get pods`

### Minikube

Minikube runs a single node cluster, compared to production kubernetes clusters which are multi-node and distributed

1. `minikube start`

1. `minikube stop`

1. `minikube delete`

1. `minikube dashboard`: Open a browser window with a locally hosted dashboard for your cluster. You can use this dashboard to view and manage your cluster.

