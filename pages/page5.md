Shop projesine ait dışarı açılan servisleri güzel bir arayüz ile dışarı açmak istiyoruz.

- https://swagger.io/
- http://springfox.github.io/springfox/

Shop projemiz bir java projesi olduğu için **springfox** projesi bizim işimizi görüyor.

Projemiz gradle projesi olduğu için bu projeyi bir kütüphane olarak projemize eklemek için yapacağımız değişiklikler.

build.gradle

dependencies
	implementation("io.springfox:springfox-swagger2:2.9.2")
	implementation("io.springfox:springfox-swagger-ui:2.9.2") // only for swagger-ui.html
}


