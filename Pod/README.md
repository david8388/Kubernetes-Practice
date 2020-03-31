# create pod
```
$ kubectl create -f <CreatedPod.yaml>
$ kubectl get po
$ kubectl describe pods <PodName>
```

# interactive with container
```
# 1. kubectl port-forward
$ kubectl port-forward <PodName> <localPort>:<PodPort>

# 2. create service
$ kubectl expose pod <PodNmae> --type=NodePort --name=<ServiceName>
```

# add label dynamically
```
$ kubectl label pods <PodNmae> <Key>=<Value>
```

