# cncf-test-prep
# CKA 

## kubernetes setup

ps auxw | grep -i kubelet
* client cert paths
* ca cert file path
* --network-plugin (e.g. cni, docker, etc)

## weave install

kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
