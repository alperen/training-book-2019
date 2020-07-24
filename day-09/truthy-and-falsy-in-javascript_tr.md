# JavaScript'te doğruluk ve yanlışlık
JavaScript'teki veri türleri eğer bir `if` koşuluna yazılırsa `Boolean` bağlamına zorlanır.`Type Coercion`. Aşağıdaki bilgileri kullanarak daha açıklayıcı kodlar yazabiliriz:
## JavaScript'te doğruluk
Aşağıdaki veri tipleri eğer bir `if` koşuluna sokulursa `true` değeri döndürürler.
```js
if (true)
if ({})
if ([])
if (42)
if ("0")
if ("false")
if (new Date())
if (-42)
if (12n)
if (3.14)
if (-3.14)
if (Infinity)
if (-Infinity)
```
## JavaScript'te yanlışlık
Aşağıdaki veri tipleri eğer bir `if` koşuluna sokulursa `false` değeri döndürürler.
```js
if (false)
if (null)
if (undefined)
if (0)
if (0n)
if (NaN)
if ('')
if ("")
if (``)
if (document.all)
```
## Doğruluk ve Yanlışlığı Kullanarak Obje Ataması Yapmak
JavaScript'te mantıksal `&&` ve `||` operatörlerini kullanarak, veriyi manupüle edebiliriz örneğin:
```js
const user = {
  age: 21
};

const username = user.name || "Alperen";
console.log(username) // Alperen
```
Yukarıdaki örnekte `username` değişkenine `user` objesinde olmayan bir nitelik çağırdık eğer `||` işaretini kullanmasaydık `username` değişkeni `undefined` olurdu. Fakat `||` işareti, veri yoksa bunu kullan anlamını taşıyor. Bunu `&&` kullanarak da yapabilirdik.

```js
const user = {
  age: 21
}

const isUserAbove18 = user.age && user.age > 18
```
Yukarıdaki örnekte ilk önce `user` objesinin `age` adında bir niteliği var mı diye kontrol ediyor evet varsa 18'den büyük mü değil mi onu kontrol ediyoruz.