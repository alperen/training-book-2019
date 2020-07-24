# Eşitlik ve Denklik
JavaScript'te iki veriyi karşılaştırmak için iki yol vardır. Birincisi, tip çevirmeli karşılaştırma `The Abstract Equality Comparison Algorithm` (`==`) ikincisi, strict (`===`, katı) tam benzerlik içerik karşılaştırması. Katı karşılaştırma, verilerin aynı içeriye ve aynı objeden üretildiği zaman `true` döndürür. Tip çevirmeli karşılaştırmada ise verilerin içeriklerin eşit olması yeterlidir. Tip çevirmeli karşılaştırma veri türlerini karşılaştırma esnasında aynı türe getirir. Aşağıdaki örneklerden hepsi `true` değeri döndürür:
```js
console.log(1 == 1);
console.log("1" == 1);
```
## Karşılaştırmanın Özellikleri

* İki `string` karşılaştırmasının doğru olabilmesi için, hedef stringler aynı uzunlukta, aynı konumlarda aynı karakterlere sahip olmak zorundadır.
* İki `number` karşılaştırmasının doğru olabilmesi için, hedef sayılar numeratik olarak birbirine eşit olmalı, işaretleri aynı olmalıdır. İkisinden biri `NaN` olmamalıdır. `NaN` değerler hiç bir zaman birbirine eşit değillerdir.
```js
console.log(1 == 1) // true
console.log(NaN == NaN) // false
console.log(NaN === NaN) // false
console.log(Infinity == Infinity) // true
console.log(Infinity === Infinity) // true
```
* İki `boolean` değer, sadece katı benzerlik ile karşılaştırılabilir.
* Birbirinden ayrık objeler karşılaştırılamaz. Objeler yalnızca aynı değişkeni referans gösteriyorlarsa `true` döndürürler. Örneğin:
```js
const a = {a: 1};
const b = {a: 1};
const c = a;
console.log(a == b) // false
console.log(a == {a: 1}) // false
console.log(a == c); // true
console.log({} == {}) // false
```
Objelerin içerikleri aynı olsa bile karşılaştırılmaları `false` döner. Yalnızca aynı değişkeni referans gösterirlerse `true` döner.
* `null` ve `undefined` değerler, tip çevirmeli karşılaştırmada `true`, katı karşılaştırmada ise `false` döndürürler.
```js
console.log(null == undefined) // true
console.log(null === undefined) // false
```

`===`, işareti verileri tip değişimine sokmadan kontrol eder. `true` döndürmesi için veriler aynı objeden doğmuş olmalı, aynı değerlere sahip olmalıdır. `switch-case` yapısı katı karşılaştırma yapar.