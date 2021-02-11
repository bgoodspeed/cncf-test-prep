# cncf-test-prep
# CKA 

## quality of life tricks

kubectl run podName --image=imageName --dry-run=client -o yaml > pod.yaml
kubectl get pod podName -n namespace -o yaml > pod.yaml
kubectl edit pod podName 
...

kubectl expose deployment -n ingress-space ingress-controller --type=NodePort --port=80 --name=ingress --dry-run -o yaml > ingress.yaml


## kubernetes setup

ps auxw | grep -i kubelet
* client cert paths
* ca cert file path
* --network-plugin (e.g. cni, docker, etc)

## cni

/etc/cni/net.d
* startup config
* type field says entrypoint

/opt/cni/bin
* cni plugins dir
* 

## weave install

kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"

## node level networking

ip link
* weave - 
* docker

ip addr

## DNS

### default name resolution
service-name
service-name.NAMESPACE
service-name.NAMESPACE.TYPE.ROOT

e.g.
db-service.prod.svc.cluster.local
db-pod.dev.pod.cluster.local

### what are you using?
kubectl get pods -n kube-system
(look for coredns-* in kube-system)


## CoreDNS
/etc/coredns/Corefile

## namespace
kubectl create namespace ingress-space
kubectl create configmap -n ingress-space nginx-configuration
kubectl create serviceaccount -n ingress-space ingress-serviceaccount

## kubeadm

need multiple systems (master node(s)), etcd HA nodes, worker nodes. install docker on all nodes.
install kubeadm on all nodes

initialize master
build pod network
join nodes to cluster

master: kubeadm init 
master: create config file from admin.conf
master: copy join token string from output
node: kubeadm join 172.17.0.19:6443 --token hl6ftb.82p3uqu1x402e3ej \
    --discovery-token-ca-cert-hash sha256:b9215358c2350ba833986ccadc981ca5f45e6efafc806613eecbcd9de3022c0c
    
