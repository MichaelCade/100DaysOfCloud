
![placeholder image](https://kubernetes.io/images/kubernetes-horizontal-color.png)

# Hands-On Practical - Kubernetes with Docker Containers

## Cloud Research

I have been reading a lot about what container engine can be used within Kubernetes and it is not only Docker but Docker seems to be top of mind and because of that it was the easiest one for me to pick up at least first. 


I have documented this really for myself to repeat over and over, but published so that people may need or want to use these steps to build out your own Kubernetes cluster, there are many walkthroughs out there though explaining really the same thing. 

In this walkthrough / post we are going to deploy some containers and get a NGINX container scaled up across my two nodes and make sure we can access the web front end. 

```
kubectl run myshell --rm -it --image busybox -- sh
kubectl create deployment nginx --image=nginx
```
Increase the number of replicas for the nginx deployment. 
```
kubectl scale deploy nginx --replicas 2
```

creating a service and exposing this to the network 
```
kubectl expose deployment nginx --type NodePort --port 80 
```

with this command you are going to understand the NodePort that you need to use to access the NGINX deployment from the worker nodes, this is very similar to the process we took for the kubernetes dashboard NodePort change. We will cover port forwarding in the next one. 

```
kubectl describe svc nginx 
```

Open a web page with your worker IP address:NODEPORT Address and you should see the NGINX opening page

now you can create a yaml file based on what you have created so far. 
```
kubectl get deploy nginx -o yaml > /tmp/nginx.yaml
```

same for the service
```
kubectl get svc nginx -o yaml > /tmp/nginx-service.yaml
```

Then you can use these yaml files to deploy and version your deployments 
```
kubectl create -f /tmp/nginx.yaml 
kubectl create -f /tmp/nginx-service.yaml 
```

if created through yaml you can delete with 
```
kubectl delete -f /tmp/nginx.yaml 
kubectl delete -f /tmp/nginx-service.yaml 
```
I have been seeing and hearing a lot about helm in this learning journey around Kubernetes over the last 12 months. The best way to describe Helm is it is a package manager for Kubernetes. Helm makes things very simple when it comes to deploying packaged applications. I am going to add this here as we will need this in the next few posts. 

Installing Helm - https://helm.sh/docs/intro/install/

curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
sudo apt-get install apt-transport-https --yes
echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt-get update
sudo apt-get install helm

In the next post we will take a look at port forwarding and how we can then use a Windows machine (other OS can be used but we will be covering Windows) to connect to our kubernetes cluster remotely. 


## Social Proof

![social image](https://pbs.twimg.com/media/ElPzSFEWkAM28LJ?format=png&name=900x900)

[Tweet](https://twitter.com/MichaelCade1/status/1320666636630765569?s=20)