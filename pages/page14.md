---
layout: default
---
# Account Projesi - Dotnet Core  Projesini Docker Konteyner Haline Getirmek


## docker image oluşturmak


```
$ git clone https://github.com/microservice-base/account.git

$ cd account

$ docker build --no-cache -t image-account -f container/docker/Dockerfile .

$ docker run -d --name app-account -p 8003:80 image-account

$ curl http://localhost:8003/api/values
$ curl http://localhost:8003/account/api/values

$ docker tag image-account:latest keramiozsoy/image-account:latest

$ docker push keramiozsoy/image-account

```

_yay_
[back](https://microservice-base.github.io/)



