# L18-04

There are two ways to create resources in kubernetes - imperative and declarative.
Let's deploy an Nginx container using both methods.

## Imperative

    kubectl create deployment mynginx1 --image=nginx

## Declarative

    kubectl create -f deploy-example.yaml

## Get list of active deployments

    kubectl get deploy

## Cleanup

    kubectl delete deployment mynginx1
    kubectl delete deploy mynginx2
