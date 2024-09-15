# Locally run your own K8s dashboard

## Prerrequisites

- You have kubernetes in docker enabled

- be sure you are in the proper cluster / context.  `kubectl config current-context` if not go to the one you want `kubectl config use-context <context-name>`


## Run dashboard

Install kubernetes dashboard (only the first time is needed)


    ```shell
    kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
    ```

 Run a Service Account (only the fist time is needed)

    ```shell
    kubectl apply -f dashboard.adminuser.yml
    ```

Get a token and copy the token into your clipboard.

    ```shell
    kubectl -n kubernetes-dashboard create token admin-user
    ```

Run the dashaboard
  
    ```shell
    kubectl proxy
    ```

1. Visit !()[http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/]
2. Paste the token into the login screen and you can then sign in to the dashboard.
