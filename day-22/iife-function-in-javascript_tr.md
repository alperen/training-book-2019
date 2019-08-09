# Javascript'te IIFE Fonksiyonlar
Tanılandığı anda çalıştırılan fonkiyonlar diye tanımlayabileceğimiz fonksiyonlar, `IIFE` (`Immediately Invoked Function Expression`) kısaltması ile anılıyor. Bu fonksiyonların gövdeleri yazıldıktan hemen sonra çalıştırılmaya başlanır. Bir tür anonim fonkiyondur ve dışarıdaki bir skop içerideki bu fonksiyona erişemez. (Eğer erişilmeye çalışan şey `return` edilmiyorsa.)

Kendi kendini çalıştıran anonim fonksiyon olarak da anılır. İki önemli kısımdan oluşur. Birinci kısımda ihtiyacımız olan fonksiyon `()` parantezleriyle sarılır. İkincisindeyse, bu fonksiyon derhal `immediately` çalıştırılır.

```js

(function () {
  console.log("It's a IIFE function.")
})();

```

Her fonksiyonun olduğu gibi, `IIFE`'nin de bir skopu vardır. Skop içindeki değişkenler dışarıya çıkamaz. `IIFE` fonksiyonları her fonksiyon gibi bir değer döndürebilir.

```js
const sayMyName = (() => {
  return "Alperen";
})();

console.log(sayMyName);
```

Bu tip fonksiyonlar gövde işlemi bittikten hemen sonra çalıştırırlar. Bu yüzden bu fonksiyonların içindeki değerlere erişmek için tekrar çalıştırmayız. Bir `computed-value` üretirler.