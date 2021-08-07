### Jenkins server setup with Helm to deploy into Kubernetes cluster

## Download and Install helm 
```sh
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 > get_helm.sh
chmod 700 get_helm.sh
./get_helm.sh -v v2.16.1
```

## Test with helm command
```sh
helm version
helm
```

## Copy config file from Kubernetes master to Jenkins home directory
```sh
mkdir /var/lib/jenkins/.kube
copy config file under .kube directory with jenkins ownership
```

## Install tiller in Kubernetes master
```sh
kubectl -n kube-system create serviceaccount tiller
```
### Next, bind the tiller serviceaccount to the cluster-admin role:
```sh
kubectl create clusterrolebinding tiller --clusterrole cluster-admin --serviceaccount=kube-system:tiller
```
## Execute below command in Jenkins server to install tiller on cluster
```sh
helm init --service-account tiller
```
## To verify that Tiller is running, list the pods in the kube-system namespace:
```sh
kubectl get pods --namespace kube-system
```







