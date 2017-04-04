### Flink on Kubernetes - deployment

## Flink 1.2 on a standalone HA deployment
This deployment is the HA deployment of Flink 1.2 described [here](https://ci.apache.org/projects/flink/flink-docs-release-1.2/setup/jobmanager_high_availability.html#configuration). HA deployments require Zookeeper. This makes it a bit much for a local dev deployment, but on the other hand we shouldn't go too far from a possible production environment when developing.
### Storage
This setup is using the `tma75/flink-stocator` image that includes the Stocator libraries to wrap swift api in a HDFS api to support object storage from Flink.
You can create an Object storage service instance on bluemix from [here](https://console.ng.bluemix.net/catalog/services/object-storage). Create a Free service instance and create credentials for it.
Make sure that the config space is updated to use your object storage service instance as follows:
```
ha.storage.dir: swift2d://<container name>.bmv3/flink-ha/
checkpoint.dir:   swift2d://<container name>.bmv3/checkpoints/
# Object storage credentials
fs.swift2d.service.bmv3.auth.url: https://identity.open.softlayer.com/v3/auth/tokens
fs.swift2d.service.bmv3.public: "true"
fs.swift2d.service.bmv3.tenant: <project id>
fs.swift2d.service.bmv3.password: <password>
fs.swift2d.service.bmv3.username: <userid>
fs.swift2d.service.bmv3.region: dallas
```
Replace `<container name>`, `<project id>`, `<password>` and `<userid>`.
### Deploy on kubernetes
For local deployment using minikube make sure that the minikube has plenty of memory as mention above. Note that resource requirements and affinity settings are removed so this should not be used for a production environment. Zookeeper is directly using the kubernetes example on stateful sets found [here](https://github.com/kubernetes/contrib/tree/master/statefulsets/zookeeper).
To create the zookeeper cluster use the following call:
```
kubectl create -f k8s/k8s-zookeeper-set.yaml
```
Once that is done the flink cluster can be added with the following call:
```
kubectl create -f k8s/k8s-flink-standalone-ha.yaml
```
This file creates 2 job managers and 4 task managers. Feel free to only use one job manager and less task managers to save memory.
#### Proxy
Since jobmanagers are added as stateful sets (to get a reliable dns record) exposing a nodeport or load balancer uses round robin between the different replicas. Since we only have one elected leader we can add our own proxy that lets you expose each jobmanager on a separate port. Start out with creating a self-signed certificate and add that as a kubernetes secret (will be mounted later). Also, password for basic auth (in this example flink/flink) is added. This step is optional, don't add the htpasswd in that case.
```
openssl dhparam -out dhparam.pem 2048
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
htpasswd -nb flink flink > htpasswd
kubectl create secret generic ssh-secret --from-file=proxycert=cert.pem --from-file=proxykey=key.pem --from-file=dhparam=dhparam.pem --from-file=htpasswd=htpasswd
```
Then deploy the proxy itself with:
```
kubectl create -f k8s/k8s-nginx-proxy.yaml
```
Jobmanager dashboards will be exposed on port 31000/31001/... on the host `$(minikube ip)`.


#### Shield engine on Flink

[Next slide: Shield on Flink](ShieldOnFlink.md)
