# Javascript'te Object Veri Tipi
Javascript'te en çok kullanılan ve doğru kullanımığında da pek çok hata ile karşılaşılan bir veri türü object. Muhtemelen üzerinde de en çok yazı yazılmış.

Javascript'te her veri türü (primitifler de dahil) bir objeden türer. Her bir objenin bir `prototype` verisi olur, bu verinin içerisinde obje içersinde bulunan fonksiyonlar ve objeye ait bilgiler vardır. Örneğin,
```js
const isim = "Alperen";

isim.toLowerCase(); /// alperen
```
`toLowerCase` gibi yardımcı fonksiyonlar, `String` objesinin prototipinde belirtilmiştir ve `String`'ten türüyen her veriye aktarılır. Bir değişkenin prototipine `[variable].__proto__` yazarak ulaşılır.

Yeni bir obje tanımlamak için değişkene `{}` tanımlaması yapılabilir. Bu değişken `Object` objesinden türer. Örneğin:

```js
const user = {
	name: "Alperen",
	surname: "Turkoz",
	age: 21,
	getFullName: () => {
		return `${this.name} ${this.surname}`
	}
}
```
Bu objenin key-value eşleşmesindeki key değerleri `property` (öznitelik) diye adlandırılır. Ve onlara iki yolla erişilebilir. `user[property]` veya `user.property` yollarını kullanarak. Ayrıca bir property fonksiyon ise `method` olarak adlandırılır. Metot fonksiyonları içinde yazılan `this` sözcüğü objectin kendisini referans eder. `this` sözcüğü Javascript'te skopa özel değiştirilir.

Yeni tanımlanmış her obje bir ön tanımlı prototip ile gelir. Bunlardan kurtulmak için `Object.create(yourObject)` söz dizimini kullanırız, böylelikle objenin prototipi boş bir şekilde gelir.

Sabit (`constant`) tanımlanmış tüm değerin öznitelikleri veya metotları değiştirilebilir örneğin:
```js
user.name = "Mahmut" // Alperen has changed into Mahmut
```
Fakat değişken sabitti bu nasıl oldu?. Javascript'te sabitler yalnızca yeniden başka bir değere eşitlenemezler, öznitelikleri vs. değiştirilebilir. Bunu engellemek için `Object.freeze(object)` kullanırız, böylelikle nitelikleri de değiştirilemez. Örneğin:
```js
const user = {
	name: "Alperen"
}

Object.freeze(user);

user.name = "Mahmut"; // Alperen has not changed because of this was freezed.

```

Object prototipinden gelen bazı fonksiyonlar vardır bunlar

Object.assign(object): İki veya daha fazla objeyi birleştirmeye yarar.
Object.keys(object): Bir objenin özniteliklerini bir array'a dönüştürür.
Object.values(object): Bir objenin değerlerini bir array'a dönüştürür.
Object.entries(object): Bir objenin değerlerini ve özniteliklerini bir array'e [key, value] şeklinde dönüştürür.

Javascript'te objeler bir işleme sokulduğunda, referanslarıyla birlikte işleme girerler örneğin:

```js
const first = {
	name: "Alperen",
	age: 21,
}
const second = first;

first.name = "Mahmut"; //First's name became Mahmut

console.log(second.name); // Puts "Mahmut" on the screen

```
Yukarıda görüldüğü gibi `second` değişkeni, `first`'e eşitlendiğinde, `first`'in değerlerini değil bellekteki noktasını aldı. Bunu çözmek için, bu yöntemi kullanırız:
```js
const second = Object.asssign({}, first);
```

Javascript, OOP destekler fakat yapılan her işlem bir objeye dönüştürüldüğünde pratikte oop javascript tarafından desteklenmez.