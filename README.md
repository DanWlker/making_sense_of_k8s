## Making sense of Kubernetes

1. `Node` is a kubernetes word for computer (can be VM, physical hardware etc)

1. `Pod`: A Pod is the smallest and simplest unit in the Kubernetes object model that you create or deploy. It represents one (or sometimes more) running container(s) in a cluster

1. `Ephemeral`: Fancy word for "temporary", pods are designed to be spun up, torn down, and restarted at a moment's notice, promotes immutability as well

1. `ReplicaSet`: Maintains a stable set of replica Pods running at any given time. It's the thing that makes sure that the number of Pods you want running is the same as the number of Pods that are actually running. (You will probably never use ReplicaSets directly)

### Kubectl

1. `kubectl get deployments`: create a deployment, needs `name` and `id of docker image`

    ```sh
    kubectl create deployment {some-deployment-name-web} --image={docker.io/username/some-docker-image:latest}
    ```

1. `kubectl get pods`

    use `-o wide` to get a wide output, including ip address

    ```sh
    kubectl get pods -o wide
    ```

1. `kubectl port-forward {pod-name} 8080:8080`

1. `kubectl edit deployment {deployment-name}`

1. `kubectl delete pod {pod-name}`

1. `kubectl logs {pod-name}`

1. `kubectl proxy`: start a proxy server on your local machine

1. `kubectl get replicasets`

### Minikube

Minikube runs a single node cluster, compared to production kubernetes clusters which are multi-node and distributed

1. `minikube start`

1. `minikube stop`

1. `minikube delete`

1. `minikube dashboard`: Open a browser window with a locally hosted dashboard for your cluster. You can use this dashboard to view and manage your cluster.
