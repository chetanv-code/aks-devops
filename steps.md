az login

az account set -s {sid}

az group create -n aks-rg -l eastus

az aks create --resource-group aks-rg  --name myAKSCluster --node-count 1 --enable-addons monitoring --generate-ssh-keys
az acr create -n cmvregistry123 -g aks-rg  --sku Standard

az aks update -n myAKSCluster -g aks-rg --attach-acr cmvregistry123

az aks get-credentials --resource-group aks-rg --name myAKSCluster



az aks start --name myAKSCluster --resource-group aks-rg
az aks stop --name myAKSCluster --resource-group aks-rg