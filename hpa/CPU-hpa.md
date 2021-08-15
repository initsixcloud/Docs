# Configure Horizontal Pod Autoscaler

## Modify deployment.yaml with Resource limits
```sh
  
          resources:
          limits:
            cpu: '1'
            memory: "500Mi"
          requests:
            cpu: '1'
            memory: "500Mi"
  ```
## hpa.yaml file in helm chart
 ```sh
  apiVersion: autoscaling/v1
kind: HorizontalPodAutoscaler
metadata:
  name: petclicnic-hpa
spec:
  maxReplicas: 5
  minReplicas: 1
  scaleTargetRef:
    apiVersion: extensions/v1beta1
    kind: Deployment
    name: petclinic-deployment
  targetCPUUtilizationPercentage: 50
  ```
## Install siege package on K8 Master

### Siege is a stress tester for HTTP/HTTPS


### If EKS Management OS is RHEL, then execute below commands
yum -y install epel-release
yum -y install siege

### If EKS Management OS is Amazon Linux, then execute below commands
sudo amazon-linux-extras install epel
yum install siege -y
```
```sh
siege -q -c 2 -t 2m http://ip:port
q = quiet mode
c = concurrent
2m = time period
```
