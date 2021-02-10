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


