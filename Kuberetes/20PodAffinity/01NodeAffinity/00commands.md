# deploy pod
kubectl apply -f 01nodeaffinity.yml

# get pods
kubectl get po -o wide
# the above one should deploy a node which contains lable of capacity=high-memory

# clean up the pods
kubectl delete -f 01nodeaffinity.yml

# create the pod again with second yaml
kubectl apply -f 02nodeaffinity.yml

# get the pods using the following
kubectl get po -o wide
# the above pod will be in a pending state. Due to the label is not available.

# clean up using the following commnd.
kubectl delete -f 02nodeaffinity.yml

# create the pod again with third yaml
kubectl apply -f 03nodeaffinity.yml

# get the pods using the following
kubectl get po -o wide
# the above pod will running state. Due to preferredDuringSchedulingIgnoredDuringExecution expression. Even though the label is missing you can have the pod running on the cluster.

# clean up using the following commnd.
kubectl delete -f 02nodeaffinity.yml
