---
layout: default
---
# Payment Projesi -  Python Projesini Docker Konteyner Haline Getirmek


## docker image oluşturmak


```
$ git clone https://github.com/microservice-base/payment.git

$ cd ui 

$ docker build --no-cache  -t image-payment  -f container/docker/Dockerfile .

$ docker run -d --name app-payment -p 8004:8004 image-payment:latest

$ docker tag image-payment:latest keramiozsoy/image-payment:latest

$ docker push keramiozsoy/image-payment

```

_yay_
[back](https://microservice-base.github.io/)
