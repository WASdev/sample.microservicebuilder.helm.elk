---

copyright:
  years: 2017
lastupdated: "2017-06-02"

---

# Troubleshooting

## Avoid trouble

### Redeploying the ELK Sample

Before you delete the existing helm deployment of the ELK sample and redeploy it, ensure that you delete the following items:
* Kubernetes secrets:
 * _mb-serer-key_
 * _mb-server-crt_
* The Kubernetes configuration map:
 * _liberty-logging-config_

To list any existing secrets, run the following command:
```
kubectl get secret
```
To list any existing configuration maps, run the following command:
```
kubectl get configmap
```
Use the following commands as appropriate:
```
kubectl delete secret name_of_secret
kubectl delete configmap name_of_configmap
```

## Solving common problems

### My Liberty server or Liberty service is not connecting to the sample ELK stack.

* Ensure that your Liberty Kubernetes deployment configures the following Kubernetes secrets and the following Kubernetes configuration map exactly like the snippets on the [configuration page](sample_elk_task.md).
  * Kubernetes secrets:
    * _mb-keystore_
    * _mb-keystore-password_
    * _mb-truststore_
    * _mb-truststore-password_
  * The Kubernetes configuration map:
    * _liberty-logging-config_

* If you are using a yaml type file for your Kubernetes configuration, ensure that you have the correct amount of spaces (not tabs) in your Kubernetes configuration file, as extra spacing can have an undesired effect. The appropriate amount is 2 spaces for _subelements_.

### I don't know the Kibana browser client URL.

* The link to the Kibana browser interface can be obtained by running the following commands:
```bash
 export NODE_PORT=$(kubectl get --namespace default -o jsonpath="{.spec.ports[0].nodePort}" services logserver)
 export NODE_IP=$(kubectl get nodes --namespace default -o jsonpath="{.items[0].status.addresses[0].address}")  
 echo http://$NODE_IP:$NODE_PORT/
```
* For the commands to work, the **kubectl** command must be able to access your Kubenetes.

### I can't view anything on the Kibana browser client. It keeps asking me about indices.

* Ensure that your Liberty server or Liberty service is configured correctly to send data to the ELK stack. See the [configuration page](sample_elk_task.md).

* In Kibana, ensure that the index pattern is _Logstash-*_ by clicking **Settings > Indices**.

* In Kibana, ensure that the Time-field name is set to _datetime_. The option to choose the Time-field name shows up on the main Kibana page after the ELK stack receives data.
