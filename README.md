# Finance API Predictor

Before the App can be built and deploy using a CI / CD pipeline based in kubernetes you need to have:

Create Cluster:

- cluster. run `eksctl create cluster --name test-cluster --nodegroup-name test-nodes --node-type t3.medium --nodes 1 --nodes-min 1 --nodes-max 1  --managed`  
- ingress controller: `kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml`
- service. run `kubectl apply -f infrastructure/service.yml`
- ingress. run `kubectl apply -f ingress.yml`

Create Service:

run `service.yml`

Create Ingress:

run `ingress.yml`

To get the external IP

    ```shell
        kubectl get service api-service
    ```

To clean up everything

run `cleanup_script.sh`


### EKS Management using eksctl

- Create a cluster

- Delete a cluster `eksctl delete cluster --name test-cluster`
- Delete all: check cleanup_script.sh

- Check Cluster status `aws cloudformation list-stacks --stack-status-filter CREATE_IN_PROGRESS CREATE_FAILED CREATE_COMPLETE ROLLBACK_IN_PROGRESS ROLLBACK_FAILED ROLLBACK_COMPLETE DELETE_IN_PROGRESS DELETE_FAILED DELETE_COMPLETE`

to get session: `aws sts get-session-token --duration-seconds 3600`
