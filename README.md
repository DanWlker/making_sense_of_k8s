# Making sense of Kubernetes

1. `Node` is a kubernetes word for computer (can be VM, physical hardware etc)

1. `Pod`: A Pod is the smallest and simplest unit in the Kubernetes object model that you create or deploy. It represents one (or sometimes more) running container(s) in a cluster

1. `Ephemeral`: Fancy word for "temporary", pods are designed to be spun up, torn down, and restarted at a moment's notice, promotes immutability as well

1. `ReplicaSet`: Maintains a stable set of replica Pods running at any given time. It's the thing that makes sure that the number of Pods you want running is the same as the number of Pods that are actually running. (You will probably never use ReplicaSets directly)

1. `Thrashing Pods`

    Usually caused by:

    - bug in the image

    - misconfigured app

    - dependency of app is misconfigured

    - app using too much memory

1. `CrashLoopBackoff`: Means container is crashing. Kubernetes is all about building self-healing systems, it will automatically restart the container. However, each time it tries to restart the container, if it crashes again, it will wait longer and longer in between restarts. That's why it's called a "backoff".

1. `ConfigMap`: are not cryptographically secure, should use [Kubernetes Secrets](https://kubernetes.io/docs/concepts/configuration/secret/) for sensitive data

## Yaml stuff, because why not

1. `apiVersion`: apps/v1 - Specifies the version of the Kubernetes API you're using to create the object (e.g., apps/v1 for Deployments).

1. `kind`: Deployment - Specifies the type of object you're configuring

1. `metadata`: Metadata about the deployment, like when it was created, its name, and its ID

    - `kubectl.kubernetes.io/last-applied-configuration`: will not be there if we do `kubectl create deployment`, but will be there after we do `kubectl apply`

### Deployments

1. `spec`: The desired state of the deployment. How many replicas you want, will be made here.

    - `replicas`: Amount of replicas

    - `selector/matchLabels/app`: should match `metadata/labels/app`

    - `template/metadata/labels/app`: should match `metadata/labels/app`

    - `containers`: stuff like `name`, `image`, `env` or `envFrom`

        - `env`: stuff like `name`, `valueFrom`

            - `valueFrom/configMapKeyRef`: to specify where to get the value from configmap, includes `name`, `key`

        - `envFrom/configMapRef`: compared to `env`, we don't have to list each env variable one by one

1. `status`: The current state of the deployment. You won't edit this directly, it's just for you to see what's going on with your deployment.

### ConfigMap

1. `data`: where you specify any key values

## Kubectl

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

1. `kubectl apply -f {configuration}.yaml`

## Minikube

Minikube runs a single node cluster, compared to production kubernetes clusters which are multi-node and distributed

1. `minikube start`

1. `minikube stop`

1. `minikube delete`

1. `minikube dashboard`: Open a browser window with a locally hosted dashboard for your cluster. You can use this dashboard to view and manage your cluster.
