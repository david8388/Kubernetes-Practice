# create secret object
1. Import file to create secret data
```
$ echo "root" > username.txt
$ echo "rootpass" > password.txt
$ kubectl create secret generic demo-secret-from-file --from-file=./username.txt --from-file=./password.txt 
secret/demo-secret-from-file created
$ kubectl get secrets
```

2. Input secret data by cmd
```
$ kubectl create secret generic demo-secret-from-literal --from-literal=username=root --from-literal=password=rootpass
secret/demo-secret-from-literal created
```

3. create secret data by yaml
```
$ echo "root"
cm9vdA=
$ echo "rootpass"
cm9vdHBhc3M

$ vi my-secret.yaml
apiVersion: v1
kind: Secret
metadata:
  name: demo-secret-from-yaml
type: Opaque
data:
  username: cm9vdAo=
  password: cm9vdHBhc3MK
```

# How to volumn secret object into Pods

1. Secret as environment variable
```
$ vi <Pod>.yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  labels:
    app: webserver
spec:
  containers:
  - name: demo-pod
    image: zxcvbnius/docker-demo
    ports:
    - containerPort: 3000
    env:
    - name: SECRET_USERNAME
      valueFrom:
        secretKeyRef:
          name: demo-secret-from-yaml
          key: username
    - name: SECRET_PASSWORD
      valueFrom:
        secretKeyRef:
          name: demo-secret-from-yaml
          key: password

$ kubectl exec -it <PodName> bash
root@my-pod:/app# echo $SECRET_USERNAME
root
root@my-pod:/app# echo $SECRET_PASSWORD
rootpass
``` 

2. Mount secrets file into specific path in pod
```
$ vi  my-pod-with-mounting-secret.yaml 
apiVersion: v1
kind: Pod
metadata:
  name: my-pod-with-mounting-secret
  labels:
    app: webserver
spec:
  containers:
  - name: demo-pod
    image: zxcvbnius/docker-demo
    ports:
    - containerPort: 3000
    volumeMounts:
    - name: secret-volume
      mountPath: /etc/creds
      readOnly: true
  volumes:
  - name: secret-volume
    secret:
      secretName: demo-secret-from-yaml

$ kubectl create -f ./my-pod-with-mounting-secret.yaml
pod "my-pod-with-mounting-secret" created
$ kubectl exec -it <PodName> bash
root@my-pod-with-mounting-secret:/app# cat /etc/creds/username
root
root@my-pod-with-mounting-secret:/app# cat /etc/creds/password
rootpass
```
