# CLOUD AWS

Using managed AWS EKS

## Steps 

Create Cluster:

- cluster. run `eksctl create cluster --name finance-api-cluster --nodegroup-name finance-api-nodes --node-type t2.micro --nodes 1 --nodes-min 1 --nodes-max 1`  
- ingress controller: `kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml`
- service. run `kubectl apply -f service.yml`
- ingress. run `kubectl apply -f ingress.yml`

Create Service:

run `service.yml`

Create Ingress:

run `ingress.yml`

To get the external IP

    ```shell
        kubectl get service api-service
    ```

It spans the following services

AWS EKS
AWS EC2 t2.micro
ELB
Elastic IP

To clean up everything

run `cleanup_script.sh` (I don" remembe exactly what is doing...)

or 

    ```shell
    kubectl delete ingress --all
    kubectl delete service --all
    kubectl delete deployment --all
    kubectl delete statefulset --all
    kubectl delete daemonset --all
    kubectl delete pod --all
    ```

## EKS Management using eksctl

- Create a cluster

- Delete a cluster `eksctl delete cluster --name test-cluster`
- Delete all: check cleanup_script.sh

- Check Cluster status `aws cloudformation list-stacks --stack-status-filter CREATE_IN_PROGRESS CREATE_FAILED CREATE_COMPLETE ROLLBACK_IN_PROGRESS ROLLBACK_FAILED ROLLBACK_COMPLETE DELETE_IN_PROGRESS DELETE_FAILED DELETE_COMPLETE`

to get session: `aws sts get-session-token --duration-seconds 3600`
