![placeholder image](https://kubernetes.io/images/kubernetes-horizontal-color.png)

# Hands-On Practical - Accessing Kubernetes Cluster from Windows Desktop

## Cloud Research

I have been reading a lot about what container engine can be used within Kubernetes and it is not only Docker but Docker seems to be top of mind and because of that it was the easiest one for me to pick up at least first. 


I have documented this really for myself to repeat over and over, but published so that people may need or want to use these steps to build out your own Kubernetes cluster, there are many walkthroughs out there though explaining really the same thing. 

In this walkthrough / post we are going to take the configuration from our kubernetes cluster and make sure that we can access it from our windows desktop machine. 

I am a big fan of chocolatey and have this as my Windows Package manager so I installed the Kubernetes-CLI on my Windows Desktop using the following command. 

```
choco install kubernetes-cli
```

We then need our Kubernetes cluster config file from our master node (I believe all nodes would have this but not actually sure) We can grab this file from the following location. 

```
$HOME/.kube/config
```

You can either use SCP to access this and take a copy of this file or you can open use VI to simply copy and paste from your terminal window. 

Then with the file or the copy you need to place this in your .kube folder location. For me this was found at. 

```
C:\Users\micha\.kube\config
```

This will then allow you to run your kubectl commands locally from your windows desktop. 

```
kubectl cluster-info 
kubectl get nodes 
```
In a previous walkthrough I also mentioned about port forwarding this method if you wish to use port forwarding instead of NodePort to access for example a the Kubernetes Dashboard the above process will be required on whatever endpoint you wish to access, the reason I chose NodePort was so that I could access from all locations on my home LAN. Port Forwarding is I believe limited to just that proxy machine. 

This process is going to outline what to do to setup the port forward to the dashboard service. 

On your windows machine run the following command this will then make the Kubernetes Dashboard available at http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/

```
kubectl proxy
```

Shorter one for today but I think this covers the fundamentals on if you were ever going to have to roll your own Kubernetes Cluster on premises, another thing I have learnt is why the public cloud offerings are so much more used over on premises configurations, I have found that this method and I have tried some other deployment methods using MicroK8s and KinD that maybe I will come back to in later learning modules but I think it is now time to go back into Cloud Training with a focus around Google Cloud Platform and without a doubt in the following 88 days we are going to be touching and exploring GKS. 


## Social Proof

![social image](https://pbs.twimg.com/media/ElWN8dxWMAAhGS-?format=png&name=900x900)

[Tweet](https://twitter.com/MichaelCade1/status/1321118428913115137?s=20)