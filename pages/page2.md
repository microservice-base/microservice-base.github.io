---
layout: default
---
## Test Yazmak


Test yazmak yazılımlarımızdaki en küçük işlem parçalarının beklenen yetenekleri sergileyip sergilemediğini kontrol etmemizi sağlayan yöntemdir.

Basitçe, test yazmayı öğrenip uygulamalarımızda kullanabilmeyi bu yazı ile amaçlıyoruz.

Java dilinde yazdığımız kodları test etmek için kullanabileceğimiz bir çatıyı öğrenmeye çalışalım.

## JUnit Framework

JUnit, Java dili ile geliştirilen uygulamalarda  kullanabileceğimiz yazılımda en küçük birimleri test etmemizi sağlayan  bir kütüphanedir.

JUnit testlerinin amacı Java sınıfını ve sahip olduğu tüm bağımlılıkları test etmek değildir.
JUnit testlerinde Java sınıfları izole edilmiş olarak düşünülür ve sınıfların işlevleri test edilir.

# https://junit.org/

Bir örnek ile ilerleyelim.

# https://github.com/junit-team/junit4/wiki/Getting-started#create-a-test

Bir sınıfımız var ve içerisinde bir metot var.

```
public class Calculator {
  public int evaluate(String expression) {
    int sum = 0;
    for (String summand: expression.split("\\+"))
      sum += Integer.valueOf(summand);
    return sum;
  }
}
```

Sınıfımızın içindeki metodun işlevini test etmek için başka bir sınıf oluşturuyoruz.

```
import static org.junit.Assert.assertEquals;
import org.junit.Test;

public class CalculatorTest {
  @Test
  public void evaluatesExpression() {
    Calculator calculator = new Calculator();
    int sum = calculator.evaluate("1+2+3");
    assertEquals(6, sum);
  }
}

```

Test eden metodu belirtmek için metodumuz üzerine **@Test** ifadesi ile belirtiyoruz.

Bu ifadeden başka test sınıfları içinde metotlarda kullanılacak başka ifadeler mevcuttur.

```
 @BeforeClass    sınıf için bir kez ve ilk olarak çalışır
 @Before         her test metodudan önce  
 @Test           test metodunun kendisindir
 @After          her test metodundan sonra
 @AfterClass     sınıf için bir kez ve en son çalışır
```

## Junit Assertion
Yazdığımız test metodumuzun içinde o metottan beklediğimiz durumu kontrol etmek isteriz.
Bunun için aşağıdaki listemizdeki elemanlar ile bu kontrolü yapabiliriz.

- https://github.com/junit-team/junit4/wiki/Assertions 


_yay_
[back](https://microservice-base.github.io/)
