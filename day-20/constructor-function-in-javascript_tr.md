# JavaScript'te Constructor Function
JavaScript'teki `Contructor Function`'lar bir obje üreten, sınıflara benzeyen fonksiyonlardır. Temelde JavaScript, sınıf gibi OOP yapılarıın desteklemez. Yazacagınız sınıflar, objelere dönüştürülür. OOP temelde bir tasarım anlayışıdır. Bu tasarımları JavaScript'te objeler üzerinde çok açıkça tasarlayabilrisiniz. `Constructor` fonksiyonların adlandırılması `PascalCase` iledir. Bu fonksiyonlar, `new` sözcüğü ile başlatılır, içinde `this` sözcüğü kullanılabilir. `this` sözcüğü o anda oluşturulmuş objeyi referans eder. Örneğin:

```js
function Dog() {
  this.name = "Popcorn";
  this.color = "Cream";
  this.numLegs = 2;
}

let myOwnPopcorn = new Dog();
```
`new` sözcüğü bir `Constructor Function` `instance`'i yaratır. Yani, `myOwnPopcorn instanceof Dog` doğru bir önermedir.

Her objenin olduğu gibi fonksiyonların da prototipi değiştirilebilir. Örneğin `Dog` fonksiyonuna `numLegs`'i prototipinden tanımlarsak, `instance` olmuş her obje için `numLegs` aynı gelir.
```js
Dog.prototype.numLegs = 2;
```

Prototipten gelen değişkenler, `hasOwnProperty` fonksiyonunda `false` değerini döndürür. Örneğin, `name` ve `color` verisi, fonksiyonun kendinden `numLegs` fonksiyonu da prototipinden gelmiş bunları `hasOwnProperty` ile test edersek:
```js
myOwnPopcorn.hasOwnProperty("name"); // true
myOwnPopcorn.hasOwnProperty("color"); // true
myOwnPopcorn.hasOwnProperty("numLegs"); // false
```

Fakat, kendi nitelikleri de, prototipinden gelen niteklikleri de `in` sözcüğü karşılığında `true` döndürür. Çünkü `in` sözcüğü, objenin prototipine kadar iner.
```js
(name in myOwnPopcorn) // true
(color in myOwnPopcorn) // true
(numLegs in myOwnPopcorn) // true
(toString in myOwnPopcorn) // true
```

`Constructor Function`, kendi içinde fonksiyonlar bulundurabilir. Bu fonksiyonlar, fonksiyona prototipinden gönderilir, örneğin:
```js
Dog.prototype.sayMyName = function () {
  return this.name
}
```