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
helm search repo ingress-nginx --versions 
```
![image](https://github.com/Abhijeetjambaldare14/ingress-nginx-with-Helm/assets/13759950/446e1968-fc32-4300-b338-d1522149b7ce)

if new version is not available update repo
`helm repo update`

From the app version we select the version that matches the compatibility matrix. </br>

```
NAME                            CHART VERSION   APP VERSION     DESCRIPTION
ingress-nginx/ingress-nginx     4.7.0           1.8.0          Ingress controller for Kubernetes using NGINX a...
```
# Install Chart
Important: only helm3 is supported

`helm install my-ingress-nginx ingress-nginx/ingress-nginx --version 4.7.0`

The command deploys ingress-nginx on the Kubernetes cluster in the default configuration.

See [configuration](https://artifacthub.io/packages/helm/ingress-nginx/ingress-nginx#configuration/) below </br>

See [helm install](https://helm.sh/docs/helm/helm_install/)  for command documentation </br>

# List of all installation through Helm

`helm list --all-namespaces`

# Second ingress on different Namespace

`helm install  ingress-qa ingress-nginx/ingress-nginx --version 4.7.0 --namespace ingress-basic --set controller.ingressClassResource.name=class1`
![image](https://github.com/Abhijeetjambaldare14/ingress-nginx-with-Helm/assets/13759950/4dbf7ed5-60b8-4d91-9b97-9ca8b25f4b2f)


# Upgrading Chart 
`helm upgrade [RELEASE_NAME] [CHART] --install`
![image](https://github.com/Abhijeetjambaldare14/ingress-nginx-with-Helm/assets/13759950/d65c601e-9f51-4031-bae1-163fdddb21df)
`helm upgrade ingress-qa ingress-nginx/ingress-nginx --version 4.4.2 -n ingress-basic`

![image](https://github.com/Abhijeetjambaldare14/ingress-nginx-with-Helm/assets/13759950/c8d2bf1f-625c-4306-840f-d6d051120c57)

See [helm upgrade](https://helm.sh/docs/helm/helm_upgrade/) for command documentation. </br>

# Uninstall Chart

`helm uninstall [RELEASE_NAME]`

This removes all the Kubernetes components associated with the chart and deletes the release.

See [helm unistall](https://helm.sh/docs/helm/helm_uninstall/) for command documentation. </br>


