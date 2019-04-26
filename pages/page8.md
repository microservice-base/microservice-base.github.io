---
layout: default
---
# Go ile yazılan projelerde url yönlendirici

Go dilindeki web projelerimizde bir url üzerinden 
 - sayfa görüntülemek
 - web servis istekleri yapmak

için bir çok kütüphaneden yararlanabiliriz.


Go dili bunu varsayılan olarak desteklemektedir.
```
https://golang.org/pkg/net/http/#HandleFunc
```
Isteğe bağlı farklı çözümler mevcuttur. Temel olanı daha kullanışlı olabilmesi için bir çok açıdan geliştirmişlerdir.

```
https://github.com/gorilla/mux

https://github.com/julienschmidt/httprouter
```

Karşılaştırmak isteyenler için;

- [net/http's ServeMux](https://www.youtube.com/watch?v=9a-WV2GVGLE?target=_blank)

- [Gorilla Web Toolkit's mux package](https://www.youtube.com/watch?v=HvkeolcijlY?target=_blank)

- [julienschmidt's httprouter](https://www.youtube.com/watch?v=LsSD917wCz0?target=_blank)

_yay_
[back](https://microservice-base.github.io/)
