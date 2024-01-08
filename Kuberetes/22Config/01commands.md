## show all the config data
kubectl config view
## only current context will be shown
kubectl config view --minify
##  the path of the kubeconfig should be
# $HOME/.kube/config

kubectl config get-clusters
kubectl config get-contexts
kubectl config current-contexts

## changes the namespace on the config ##
kubectl config set-contexts --current --namespace=dev 
kubectl config set-contexts $(kubectl config current-contexts) --namespace=dev

## switch contexts
kubectl config use-contexts <contextName>