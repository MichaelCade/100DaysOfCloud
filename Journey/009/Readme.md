
![placeholder image](https://kubernetes.io/images/kubernetes-horizontal-color.png)

# Hands-On Practical - Kubernetes Dashboard

## Cloud Research

Before we start this I have to give a massive shout out to "Just me and Opensource" this guy has some amazing walkthrough YouTube tutorials and gets into the weeds and when I was working through the Kubernetes.IO documentation he came to the rescue with the a video demo on how to get things working. 

[If you want to check out his stuff you can find him here](https://www.youtube.com/channel/UC6VkhPuCCwR_kG0GExjoozg)

So today we have a Kubernetes Cluster up and running on 3 VMs running in my home lab on Microsoft Hyper-V. 

[Dashboard setup video can be found here also from "Just me and Opensource"](https://www.youtube.com/watch?v=6MnsSvChl1E)

Let's first make sure our cluster is looking good and everything is in place. 

```
kubectl cluster-info
kubectl get nodes 
```

run the following to confirm that we do not have something already occupying the same namespace we are going to use for the dashboard. 
```
kubectl get ns
```

If everything is reporting back well and good then we can continue with the dashboard deployment. 

```
kubectl create -f https://raw.githubusercontent.com/kubernetes/dashboard/master/aio/deploy/recommended/kubernetes-dashboard.yaml
```

Next we want to test we can actually access the dashboard so first we need to confirm that the dashboard service is running. 

```
kubectl -n kubernetes-dashboard get all
``` 

You will notice here that it will have a type field and depending on how you wish to access the dashboard this can be modified or used. In my environment I want to be using NodeIP to access the dashboard but you could also use port forwarding which I will cover likely in the next walkthrough. 

We can get more information about the specific service by running the following commands: 

```
kubectl -n kubernetes-dashboard describe service kubernetes-dashboard
kubectl -n kube-system describe service kubernetes-dashboard
```

to change from ClusterIP to NodePort you will run the following commands and make the relevant changes. 

```
kubectl -n kubernetes-dashboard edit svc kubernetes-dashboard
kubectl -n kube-system edit service kubernetes-dashboard
```

confirm the changes with the following 

```
kubectl -n kubernetes-dashboard get svc
kubectl -n kube-system get service
``` 

## Service Account creation
There is a service account created with the above YAML from kubernetes.io called Kubernetes-Dashboard but this will not have the relevant or required permissions to be able to really do anything within the cluster and the dashboard.  

We can now that we have the NodePort configuration complete we can now or should be able to access the dashboard with our existing limited service account. 

```
kubectl -n kubernetes-dashboard get sa
```

for more details you can use 

```
kubectl -n kubernetes-dashboard describe sa kubernetes-dashboard
```
Take the token name and use here at the end of the command, you are then going to get the token used to authenticate on the web page.

```
kubectl -n kubernetes-dashboard describe secret kubernetes-dashboard-token-m5gw8
```
So now we see that we can access the dashboard but it is likely filled with errors on which you have no permissions to do much in the dashboard. Let's fix that. 

Another shout out here to this guy, he had already created the service account yaml file I needed for a more authenticated service account. 

```
git clone https://github.com/justmeandopensource/kubernetes
```
Navigate to the dashboard folder and you will see an sa_cluster_admin.yaml modify this using VI and make sure it looks like the below 

```
apiVersion: v1
kind: ServiceAccount
metadata:
  name: dashboard-admin-new
  namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: dashboard-rolebinding
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
- kind: ServiceAccount
  name: dashboard-admin-new
  namespace: kube-system
  ```

  Then we can create our new service account based on that yaml file

  ```
kubectl create -f sa_cluster_admin.yaml
```

now if we check all available service accounts we will now see the new service account created and listed.

```
kubectl -n kube-system get sa
```

lets get that token name again with the following

```
kubectl -n kube-system describe sa dashboard-admin
```
and then use that to get the token 

```
kubectl -n kube-system describe secret dashboard-admin-token-kn7hd
```
You will now be able to access the Kubernetes dashboard on all node addresses https://Node IP Addresses:30807/ and then be able to authenticate with the token in the last command. You will see much more information regarding the cluster than you did on that first service account. 

I have documented this really for myself to repeat over and over, but published so that people may need or want to use these steps to build out your own Kubernetes cluster, there are many walkthroughs out there though explaining really the same thing. 


## Social Proof

![social image](https://pbs.twimg.com/media/ElProWPXUAAcSg-?format=jpg&name=medium)

[Tweet](https://twitter.com/MichaelCade1/status/1320658491095326726?s=20)
