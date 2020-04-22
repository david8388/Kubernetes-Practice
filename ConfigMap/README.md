# create config 
1. import config file
```
$ kubectl create configmap <ConfigName> --from-file=<ConfigFile>
configmap/redis-config created
```

2. Using cmd
```
$ kubectl create configmap <ConfigName> --from-literal=<Settings>
```

# Configuration Nginx
```
$ kubectl create configmap nginx-conf --from-file=my-nginx.conf
configmap/nginx-conf created
$ kubectl create -f ../Pod/my-third-pod.yaml
$ kubectl expose pod apiserver --port=80 --type=NodePort
service/apiserver exposed
```
