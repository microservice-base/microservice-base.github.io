---
layout: default
---
# Ui Projesi - React  Projesini Docker Konteyner Haline Getirmek


## docker image oluşturmak


```
$ git clone https://github.com/microservice-base/ui.git

$ cd ui 

$ docker build --no-cache  -t image-ui  -f container/docker/Dockerfile .

$ docker run -d --name app-ui -p 8005:3000 image-ui:latest

$ docker tag image-ui:latest keramiozsoy/image-ui:latest

$ docker push keramiozsoy/image-ui

```

_yay_
[back](https://microservice-base.github.io/)
