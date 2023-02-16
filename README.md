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
2. Create your nodes. At your terminal enter the following command: `k3d cluster create -s 2 -a 3`
3. Confirm your nodes have been created by entering the following: `kubectl get nodes`
4. Lets get important configuration information so that we can later operate our cluster. First, go to your terminal and enter the following command: `cat ~/.kube/config`. This will print the contents of your kubeconfig. Copy this information.
5. We'll use lens to operate our cluster. Launch lens and click on Catalog. Under Catagories, click on Clusters. At the bottom right, you can add your cluster via the plus icon. Hover over the icon to get more options and click on "add from kubeconfig". Paste your copied `kubeconfig`. A new menu items under Clusters has been added. You should now be able to access your cluster via your dashboard.

## References