# DataMechanics / JupyterHub integration example

This is an example integration of the DataMechanics platform in JupyterHub.

WARNING: this is for educational purposes only. The JupyterHub installation
will give unauthenticated access to your cluster.

## Install prerequesites

- [helm](https://helm.sh/)
- A working Kubernetes cluster

## Generate an API key

Navigate to your DataMechanics control plane, and generate an API key.

## Install JupyterHub on your cluster

```shell
$ make install
```

## Try your JupyterHub installation

Retrieve the public IP of your JupyterHub:

```shell
$ kubectl get service --namespace jupyterhub
NAME           TYPE           CLUSTER-IP       EXTERNAL-IP     PORT(S)        AGE
hub            ClusterIP      172.20.142.143   <none>          8081/TCP       7h46m
proxy-api      ClusterIP      172.20.29.114    <none>          8001/TCP       7h46m
proxy-public   LoadBalancer   172.20.234.80    <THE_PUBLIC_IP> 80:31789/TCP   7h46m
```

Navigate to https://\<THE_PUBLIC_IP\>/, put the address of your DataMechanics
control plane (suffixed with `/notebooks`), and the API key you generated.

Start a notebook and check its status in your DataMechanics control plane.
