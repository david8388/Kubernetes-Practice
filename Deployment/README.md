# create deployment
```
$ kubectl create -f <Deployment.yaml>
$ kubectl get po
# ReplicaSets will be created when user is deploy deployment.yaml
$ kubectl get rs
```

# expose deployment object
```
$ kubectl expose deploy <DeploymentName> --type=NodePort --name=<ServiceName>
```

# update image
```
$ kubectl set image deploy/<DeploymentName> <PodName>=<DockerAccount>/<DockerRepo>:<Version>
# if you want to record the command append --record at the end
$ kubectl set image deploy/<DeploymentName> <PodName>=<DockerAccount>/<DockerRepo>:<Version> --record
# undo rollout
$ kubectl rollout undo deployment <DeploymentName>
# check rollout history
$ kubectl rollout history deploy <DeploymentName>
# to check version
$ kubectl rollout status deploy <DeploymentName>
```
