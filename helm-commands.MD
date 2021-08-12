# Add stable to helm

```sh
helm repo add stable https://charts.helm.sh/stable
helm repo search <chartname>

helm install repo stable/<chartname> <releasename>
  
helm pull <chartname>
  
helm package <chartname>

helm uninstall RELEASE_NAME
```
