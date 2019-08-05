# Javascript'teki Veri Tipleri
Diğer dillere nazaran Javascript'te değişkenlerin değil değişken değerlerinin bir veri türü vardır. Eğer değişkeniniz, `let` veya `var` sözcüğü ile tanımlandıysa, değişken verisini değiştirdiğinizde türünü de değiştirirsiniz. Bu yüzden tip zorlaması yoktur. Javascripte primitif tipler:

* Boolean (True / False)
* Null		(Boş)
* Undefined (Tanımlı ama değeri yok)
* Number
* String
* Symbol

Bunlar dışındaki diğer tüm türler `Object` olarak adlandırılır. Yukarıdaki türler `Immutable`'dır. Değer ile taşınırlar, `Object` türündeki bütün değişkenler referanslarıyla birlikte dolaşır.

## Tanımlama örneği

```js
const v1 = "Alperen"
const v2 = true
const v3 = null
const v4 = undefined
const v5 = 15
const v6 = new Symbol("Symbols are complex to describe")
```

Javascript'te `typeof [value]` fonksiyonu, kendisine verilen değeri string olarak döndürür. Örneğin `typeof [a-variable]` yazdığınızda, değişkenin değerini ölçer, değişkenlerin tipi yoktur. Yalnızca değerlerin tipi vardır. Yine aynı şekilde bir değerin de tipini öğrenebilirsiniz: `typeof [value]`

```js
typeof v1; // returns "string" as string
typeof v2; // returns "boolean" as string

typeof 15; // returns "number" as number

typeof null // returns "object"

if (typeof v1 === "string") // This query is valid
```
Diziler, objeler, sınıflar javascript'te bir objedir. Ayrıca her bir primitif tip için bir obje oluşturabilir.

Eğer bir `null` tipindeki değişkenini kontrol ederseniz, `null` dönmesini beklerken `object` döndüğünü görürsünüz. Bu bir javascript bug'udur.

```js
const array = [1, 2, 3];
const obj = {
	key: "value",
}
typeof array; // object
typeof obj; // object

const string = new String("Alperen");

typeof string; // object
```

Görüldüğü üzere, primitif bir tip olan String bir obje olarak başladığında, `string` olarak değil `object` olarak anılmaya başlandı. Bu çok kullanılan bir yöntem değil. Hatta önerilmez. Bu tip bir `object` olarak başlatılan ifadelerin gösterdiği veri türünü anlamak için `instanceof` sözcüğünü kullanırız. Bu sözcük, değişkenin ya da verinin hangi objeden türediğini gösterir, primitif tipini değil.
```js
const string = new String("Alperen");
string instanceof String // returns true as boolean
typeof string // returns object as string
```

```js
typeof NaN; // returns Number :)
```