---
layout: default
---
# Go ile yazılan projelerde bağımlılık yönetimi - 


## yeni bir bağımlılık eklemek

dep programı komutların çalıştırılacağı bilgisayarda yüklü olmalıdır.

https://github.com/golang/dep

Yüklediğimizden emin olmak için terminalden şu komutu çalıştıralım.

```
dep version

```
Ardından projemizde bir klasör seçelim ve komutu çalıştıralım.

```
dep init

```

Komut çalıştıktan sonra iki adet dosya oluşur.

```
Gopkg.toml

Gopkg.lock
```

Projemize yeni kütüphaneleri ekleyebiliriz. 

```
https://github.com/naoina/go-stringutil
```
Örnek projemizin adresi yukarıdadır fakat ekleme komutunu çalıştırırken http ve https kısmı olmadan yazıyoruz.

```
dep ensure -add github.com/naoina/go-stringutil
```
_yay_
[back](https://microservice-base.github.io/)
