## create cluster with 2 nodes.
# 1st Node give the label as capacity=high-memory
# 2nd Node give the label as capacity=high-cpu

# Get all the nodes
kubectl get nodes

# Assign labels
kubectl label node aks-agentpool-64579358-vmss000000 capacity=high-memory
kubectl label node aks-agentpool-64579358-vmss000001 capacity=high-cpu

# Get all nodes with labels
kubectl get nodes  --show-labels=true

# Get labels for a specific node
kubectl get nodes aks-agentpool-64579358-vmss000000 --show-labels=true

#  Get labels for a specific node with filters
kubectl get nodes aks-agentpool-64579358-vmss000000 --show-labels=true | grep capacity
kubectl get nodes aks-agentpool-64579358-vmss000001 --show-labels=true | grep capacity