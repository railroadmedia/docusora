# Sysops Overview

## Kubernetes Setup

### Setup EKS

### Setup K8 Inside EKS
Diagram for K8 setup (yed live chart):
[https://gist.github.com/calebfavor/e8fe1138b8fb2a7105a4d1ea21ba68f1](https://gist.github.com/calebfavor/e8fe1138b8fb2a7105a4d1ea21ba68f1)
[https://www.yworks.com/yed-live/?file=https://gist.githubusercontent.com/calebfavor/e8fe1138b8fb2a7105a4d1ea21ba68f1/raw/40eb561a39c227afb89f2247fd8d042cf138915c/Musora%20Applications%20Back%20End%20K8%20Setup](https://www.yworks.com/yed-live/?file=https://gist.githubusercontent.com/calebfavor/e8fe1138b8fb2a7105a4d1ea21ba68f1/raw/40eb561a39c227afb89f2247fd8d042cf138915c/Musora%20Applications%20Back%20End%20K8%20Setup)

**NGINX Ingress & Deployment/Controller**
1. Create a namespace for the entire k8 setup (yaml file probably already exists) (we'll just use one for all brands)
```kubectl create -f /railkubernetes/kubernetes/eks/app-staging-environment/rk-namespace.yaml```
1. Make sure you have the helm chart
```helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx```
2. Create a new release using the values/config file in the railkubernetes repo:
```helm install -f /railkubernetes/kubernetes/eks/app-staging-environment/primary-ingress-nginx-controller-and-service-helm-values.yaml primary-ingress-nginx-c-s ingress-nginx/ingress-nginx --namespace rk```
2.5. If you ever need to update the helm release use:
```helm upgrade -f /railkubernetes/kubernetes/eks/app-staging-environment/primary-ingress-nginx-controller-and-service-helm-values.yaml primary-ingress-nginx-c-s ingress-nginx/ingress-nginx --namespace rk```
3. Create the k8 app ingress config from the file:
```kubectl apply -f /railkubernetes/kubernetes/eks/app-staging-environment/app-ingress.yaml```
4. Create an apps k8 stuff using the entire folder (musora in this example):
```kubectl apply -f /railkubernetes/kubernetes/eks/app-staging-environment/musora```


### Connecting to the Clusters
Connecting to the EKS cluster in CLI:
- From railkubernetes container in railend:  
```aws configure``` must use calebs root creds for now  
```aws eks --region us-east-2 update-kubeconfig --name musora-testing-cluster```

### SSL Termination

- Requests are sent through the entire stack encrypted (top layer like cloudflare, nginx ingress, services)
- The SSL gets terminated by apache which runs inside our app pods (php and apache): webdevops/php-apache:7.3 
(see app repos Dockerfile)
- SSL certs are stored as k8 secrets
- They get mounted to the pod under path: /ssl
- The deployment command copies them to the directory that apache looks for (php & apache run on the app pods)
- Deployment command string that does this:  
```cp /ssl/tls.crt /opt/docker/etc/httpd/ssl/server.crt && yes | cp /ssl/tls.key /opt/docker/etc/httpd/ssl/server.key```

We could update the apache config files in the app repos by overwriting the /opt/docker/etc/httpd/vhost.ssl.conf file to
change the path to just use /ssl, that would be better. TODO.