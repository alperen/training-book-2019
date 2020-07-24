# Set Objesi
Set objesi aynı diziler gibi çalışan bir JavaScript global objesidir. Set objelerinin matematiksel karşılığı kümelerdir. Set objesi her türlü veriyi, primitif tipleri, obje referanslarını içerisinde tutabilir. Dizilerden farkı, bir nesne en fazla bir kere tekrar edebilir.

Bir set oluşturmak ve ona elemanlar eklemek:
```js
const mySet = new Set();

mySet.add("Alperen");
mySet.add("Turkoz");
mySet.add("Alperen");
mySet.add({});

mySet.size; // 3
```
Benzersiz üyeleri sayarken `===` eşitliğinin sağlamasını yapar. Objeler bu sağlamada `false` döndürdüğünden aynı objeden birden fazla olabilir.

* `Set.has()` fonksiyonu bir `Set`'te belirtilen elemanın olup olmadığını kontrol eder: `mySet.has("Alperen") // true`
* `Set.clear()` fonksiyonu bir kümenin içini boşaltır.
* `Set.values()` fonksiyonu küme içindeki elemanları bir `Iterator` objesine yani döngüye aktarır.
* `Set.delete(value)` fonksiyonu verilen `value` değerini kümeden çıkarır.