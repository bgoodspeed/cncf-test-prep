# cncf-test-prep
# CKA 

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

service-name
service-name.NAMESPACE
service-name.NAMESPACE.TYPE.ROOT

e.g.
db-service.prod.svc.cluster.local
db-pod.dev.pod.cluster.local

## CoreDNS
/etc/coredns/Corefile


