# Upgrade Cluster K8s

## Cluster Master

kubectl drain kubernetes01 —ignore-daemonsets

kubectl cordon kubernetes01

sudo apt update 

sudo apt install kubeadm=1.20.0-00

sudo kubeadm upgrade plan

sudo kubeadm upgrade apply v1.20.0

apt install kubelet=1.20.0-00

systemctl stop kubelet

systemctl start kubelet

systemctl status kubelet

kubectl get nodes

kubectl cordon kubernetes01

## Cluster Worker

kubectl drain kubernetes01 —ignore-daemonsets

kubectl cordon kubernetes01

sudo apt update 

sudo apt install kubeadm=1.20.0-00

sudo kubeadm upgrade node

apt install kubelet=1.20.0-00

systemctl stop kubelet

systemctl start kubelet

systemctl status kubelet

kubectl get nodes

kubectl cordon kubernetes01