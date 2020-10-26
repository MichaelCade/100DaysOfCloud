
![placeholder image](https://kubernetes.io/images/kubernetes-horizontal-color.png)

# Hands-On Practical - Kubernetes 

## Cloud Research

Documenting here that there has been quite a gap between the last update here to now, this is because real work got in the way. More so because of the time factor to document than actually still getting to play around with stuff and getting hands on. 

As a company we purchased a data management vendor for Kubernetes data protection, and something I started last summer was the Summer Learning Journey of learning more about Cloud Native and Kubernetes so where I started this journey as a Google Cloud Learning curve I had to jump over to Kubernetes and document some findings here. I am hoping that this still counts towards the 100DaysOfCloud I believe it does and we will get back to the GCP learning curve later on. 

First of all, homelab (yes not cloud but the premise of the learning was cloud based and I had local resource I wanted to learn the hard way) I sold my homelab in the summer so I now only have a modest HPE ML110 server which is running as my backup server as well as hosting Microsoft Hyper-V (I know, I know) however on that host I decided to provision 3 Ubuntu 20.04 VMs to be used as my kubernetes master and 2 worker nodes. 

Once I had ran through the super easy installation of Ubuntu 20.04 on each of the systems I needed to install everything required to get the Kubernetes Cluster up and running. 

The following is to be ran on each of the Ubuntu nodes. 

```
sudo -i 

apt-get update 

apt-get install -y docker.io 

apt-get update 

apt-get install -y apt-transport-https curl 

curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
cat <<EOF >/etc/apt/sources.list.d/kubernetes.list
deb http://apt.kubernetes.io/ kubernetes-xenial main
EOF

apt-get update 

apt-get install -y kubelet kubeadm kubectl

sudo swapoff -a
```
For Kubernetes to run we also need to turn off the swap file feature this is what the last command above allows us to do, however if a reboot occurs then it will start again so we must permantently turn off the swap file usage wit hthe following 

```
#you need to comment out #/swapfile, escape and :wq
vi /etc/fstab 

sudo rm -f /swapfile 

#add the following line, I added to the bottom of the file and added a comment #Kubernetes for reference. net.bridge.bridge-nf-call-iptables = 1 
#escape and :wq
vi /etc/sysctl.conf
```
Finally we need to enable the docker service by running 

```
sudo systemctl enable docker.service
```

On the Kubernetes master you create your Kubernetes cluster by running the following command on only the master node. 

```
sudo kubeadm init
```
When the above command is complete you will need to follow the instructions given. The first one is to create the config directory which can then be later used to connect as a regular user from a remote machine. 

```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```
At this stage also before adding worker nodes I wanted to add a CNI provider, there are many but for this configuration I went with weave. This can be installed on the master node with the following: 

```
kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
```

Second job is to take the kubeadm join command and use this on the two remaining or more nodes for your cluster. 

```
kubeadm join 192.168.169.200:6443 --token 5auxv4.26************90 --discovery-token-ca-cert-hash sha256:01e5ef2c************************************************6a4ff89564
```

At this point or at least in a few minutes you should be able to see that you have a fully functional Kubernetes cluster using the following commands. 

```
kubectl cluster-info
kubectl get nodes 
```
if you do not see status READY then either wait a little longer or you may need to begin troubleshooting. 

You can find out more information as part of that troubleshooting using the following 

```
kubectl describe nodes
``` 

I have documented this really for myself to repeat over and over, but published so that people may need or want to use these steps to build out your own Kubernetes cluster, there are many walkthroughs out there though explaining really the same thing. 


## Social Proof

![social image](https://pbs.twimg.com/media/ElPjT5YXIAABSG4?format=png&name=900x900)

[Tweet](https://twitter.com/MichaelCade1/status/1320649350893232130?s=20)
