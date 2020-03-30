# RUN containerized app in local
```
$ docker run -p <localPort>:<containerPort> -it <ImageID>
```

# Rename Image Tag

```
# find the image id
$ docker image ls

# docker tag, beacause the following cmd will given latest tag
$ docker tag <ImageID> <DockerAccount>/<DockerRepo>

# Given tag(e.g: v2.0.0)
$ docker tag <ImageID> <DockerAccount>/<DockerRepo>:v2.0.0

# Check image
$ docker image ls
REPOSITORY                  TAG                 IMAGE ID            CREATED             SIZE
hsienwu830808/docker-demo   v2.0.0              bae982f8ffc9        9 hours ago         91.3MB
node                        12.16.1-alpine      f77abbe89ac1        7 days ago          88.1MB

# Push to dockerhub
$ docker push <DockerAccount>/<DockerRepo>

```
