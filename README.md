# ingress-nginx-with-Helm
NGINX Ingress Controller
## NGINX Ingress Controller 

You can find the [Kubernetes NGINX documentation here](https://kubernetes.github.io/ingress-nginx/) </br>

First thing we do is check the compatibility matrix to ensure we are deploying a compatible version of NGINX Ingress on our Kubernetes cluster </br>

The Documentation also has a link to the [GitHub Repo](https://github.com/kubernetes/ingress-nginx/) which has a compatibility matrix </br>

### Get the installation YAML

The controller ships as a `helm` chart, so we can grab version `v1.8.0` as per the compatibility
matrix. </br>

From our container we can do this:

```
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo list
![image](https://github.com/Abhijeetjambaldare14/ingress-nginx-with-Helm/assets/13759950/0eb43f2f-1b94-4755-a7a3-e17d947c9ab3)
helm search repo ingress-nginx --versions 
```
if new version is not available update repo
`helm repo update`

From the app version we select the version that matches the compatibility matrix. </br>

```
NAME                            CHART VERSION   APP VERSION     DESCRIPTION
ingress-nginx/ingress-nginx     4.7.0           1.8.0          Ingress controller for Kubernetes using NGINX a...
```
