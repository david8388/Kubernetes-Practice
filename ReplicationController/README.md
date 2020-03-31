# Please use spaces instead of tabs
- [YAML error: found character that cannot start any token] (https://github.com/moraes/config/issues/1#issuecomment-18842169i)

# create ReplicationController(rc)
```
$ kubectl create -f <ReplicationController.yaml>
$ kubectl get rc
$ kubectl get po
```

# delete rc
```
$ kubectl delete rc <ReplicationControllerName>
```

# if you want to pod still running after replication-controller delete.
```
$ kubectl delete rc <ReplicationControllerName> --cascade=false
```
