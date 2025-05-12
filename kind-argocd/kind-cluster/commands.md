- Create Kind cluster

  ```bash 
  kind create cluster --name k8s-playground --config config.yml
  ```

- Context list

    ```bash
    kubectl config get-contexts
    ```

- Current context

    ```bash
    kubectl config current-context
    ```

- Set context

    ```bash
    kubectl config use-context my-cluster-context
    ```

- Cluster info

    ```bash
    kubectl cluster-info --context kind-kind
    ```
    ```bash
    kubectl get nodes
    ```
    ```bash
    kind get clusters
    ```

- Create namespace for argocd resources

    ```bash
    kubectl create namespace argocd
    ```
- Install argocd

    ```bash
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    ```

- Verify installation
    ```bash
    kubectl get svc -n argocd
    ```
- Configure 
    ```bash
    kubectl patch svc argocd-server -n argocd -p '{\"spec\": {\"type\": \"NodePort\"}}'
    ```

    ```bash
    kubectl port-forward -n argocd service/argocd-server 8443:443 
    ```

- Password to login in with user name `admin`
    ```bash
    kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo
    ```

- Delete Cluster
    ```bash
    kind delete cluster --name=kind
    ```





