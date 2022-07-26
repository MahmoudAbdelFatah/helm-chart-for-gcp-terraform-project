# Helm

## This is repo for the helm chart of the gcp terraform app on this [repo](https://github.com/MahmoudAbdelFatah/GCP-with-terraform) 

> Create a Helm chart with `helmGCPChart` name. then, inside the directory of the Helm chart, run this command so 
install the chart.
>
- ` $ helm install release1 .`


# Questions's answers:
##### Deploy Jenkins Chart on the cluster and login to jenkins:
1. Get Repo Info

``` bash
$ helm repo add jenkins https://charts.jenkins.io
$ helm repo update
```

2. Install Chart

``` bash
$ helm install myjenkins jenkins/jenkins
```

3. Edit service file to expose with `NodePort` service on the `minikube` cluster.

``` bash
$ kubectl edit svc myjenkins
```
 - set type of the service to be `NodePort`, then set the `nodePort:30553` from `port` section.
 - get the minikube ip by using this command `minikube ip`.
 - now i can expose the jenkins chart which is deployed on clustet minikube by this url `minikube-ip:30553`
 
![This is a alt text.](/images/image1.png)


- Get your `admin` user password by running:

```
echo $(kubectl get secret --namespace default myjenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode)
```
![This is a alt text.](/images/image2.png)
