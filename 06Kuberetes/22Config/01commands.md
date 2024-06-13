## show all the config data
kubectl config view
## only current context will be shown
kubectl config view --minify
##  the path of the kubeconfig should be
# $HOME/.kube/config

kubectl config get-clusters
kubectl config get-contexts
kubectl config current-context

## changes the namespace on the config ##
kubectl config set-context --current --namespace=dev 
kubectl config set-context $(kubectl config current-context) --namespace=dev

## switch contexts
kubectl config use-context devakscluster