# Combining Node Affinity and Taints and Tolerances

## Problem statement

There are three Pods "blue", "white", and "green". There are three nodes A, B, and C. 

I want to make sure that pod "blue" goes to Node A
,, ,,  ..................... "white" goes to Node B
,, ,, ...................... "green" goes to Node C

Make sure that no other should be assigned to any of these nodes.


## Solution

**Create three worker nodes**

```
minikube node add -p kube
minkube node add -p kube
minikube node add -p kube
```

This should add three nodes to exising minikube kubernetes cluster.

**Assign Taints to nodes**

```
k taint node kube-m02 type=A:NoSchedule
k taint node kube-m03 type=B:NoSchedule
k taint node kube-m04 type=C:NoSchedule
```

Tainting will prevent scheduler from assigning any other pods to these nodes.

**Assign labels**

```
k label node kube-m02 node=A
k label node kube-m03 node=B
k label node kube-m04 node=C
```

This will make pods with defined affinities to be assigned to these nodes.
