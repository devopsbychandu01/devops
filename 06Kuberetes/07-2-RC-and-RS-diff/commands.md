## RC
kubectl apply -f 01pod.yaml
kubectl get pods --show-labels
kubectl apply -f 02RC.yaml
kubectl get rc
kubectl get pods --show-labels
kubectl delete rc nginxrc
kubectl delete pods static-web2

## RS
kubectl apply -f 01pod.yaml
kubectl get pods --show-labels
kubectl apply -f 03RS.yaml
kubectl get rs
kubectl delete rs nginxrs
kubectl delete pods static-web1

## Advantages of RS
kubectl apply -f 01pod.yaml
kubectl get pods --show-labels
kubectl apply -f 04RS.yaml
kubectl get rs
kubectl get pods --show-labels
kubectl delete rs nginxrs