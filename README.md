# kube-demo

Application for demonstrating kubernetes.

## Dependencies

Ensure you have the following tools installed locally:

- kubectl
- k3d
- helm
- Docker Desktop
- lens

## Setup

1. Start Docker desktop and allow it to run in the background.
2. Create your nodes. At your terminal enter the following command:

    ```bash
    k3d cluster create -a 2
    ```

3. Confirm your nodes have been created by entering the following: `kubectl get nodes`
4. Let's get important configuration information so that we can later operate our cluster. First, go to your terminal and enter the following command: `cat ~/.kube/config`. This will print the contents of your kubeconfig. Copy this information.
5. We'll use lens to operate our cluster. Launch lens and click on Catalog. Under Catagories, click on Clusters. At the bottom right, you can add your cluster via the plus icon. Hover over the icon to get more options and click on "add from kubeconfig". Paste your copied `kubeconfig`. A new menu items under Clusters has been added. You should now be able to access your cluster via your dashboard.
6. Using helm, we can add services to our cluster. Let's add a monitoring tool:

    ```shell
    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts\nhelm repo update.
    ```

     ```shell
    helm install prom prometheus-community/kube-prometheus-stack
    ```

7. We can then spin up an exmaple app on our cluster.

    ```shell
    kubectl create -f example-voting-app/k8s-specifications/
    ```

8. We'll need to port forward in order to access our app in a browser:

    ```shell
    kubectl port-forward svc/result 5001:5001
    ```

- Teardown
kubectl delete -f example-voting-app/k8s-specifications/

## References