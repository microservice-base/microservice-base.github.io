$ git clone https://github.com/microservice-base/account.git

$ cd account

$ docker build --no-cache -t image-account -f container/docker/Dockerfile .

$ docker run -d --name project-account -p 8003:80 image-account

$ curl http://localhost:8003/api/values

$ docker tag image-account:latest keramiozsoy/image-account:latest

$ docker push keramiozsoy/image-account
