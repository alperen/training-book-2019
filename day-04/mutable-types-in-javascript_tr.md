# JavaScript'teki Değişebilir Veri Tipleri
Bir önceki yazıda belirtilen primitif tipler dışında kalan her veri tipi JavaScript'te bir
`object`'ten türer. Fonksiyonlar, Objeler, Diziler bunlardan en çok kullanılanlarıdır.

## Sabit Değişkenler Tanımlamak

JavaScript'te sabit olarak adlandırılan değişkenlerin önüne `const` sözcüğü yazılarak tanımlanırlar. `const` sözcüğü, değişkeninizi değişmez yapar (`immutable`), sabit değil.
Örneğin:

```js
const isItRaining = false

isItRaining = true // Error: Assignment to constant variable.
```
Görüldüğü üzere, sabit değişkenler bir daha `=` işareti ile yeni değere sahip olamazlar. Ama diziler, objeler gibi değişkenlerin elemanları bundan etkilenmez.

```js
const person = {
  name: "Alperen",
  age: 21
}

person.age = 22 // This could be.
person = {
  name: "Mahmut",
  age: 18
} // This can't. Constants connot reassignable.

```


## Array
```js
const exampleArray = [2, true, "Hello"];
```
Diziler, birden fazla veriyi tek bir değişkende tutmamıza yardımcı olur, görülebileceği üzere JavaScript'te bir dizi içerisinde farklı tipte veriler tutulabilir. Bu yüzden bir kısıtlama yoktur.

```js
typeof exampleArray === "object" // true
exampleArray instanceof Array // true
```

## Object
```js
const exampleObject = {
 key: "Value",
 age: 21,
 isActive: true
};
```
Objeler, aynı diziler gibi bir değişken üzerinde birden fazla değişken tutmaya yarar, dizilerden farklı olarak, diziler verileri indis adı verilen sayılarda tutarken, objelerde bu string, dizi vs. olabilir.

```js
typeof exampleArray === "object" // true
exampleArray instanceof Object // true
```

Object, Array, Function gibi tipler yukarıda görüldüğü gibi bir primitif tipmiş gibi tanımlanabildiği gibi aynı zamanda bir `constructor` yardımı ile de tanımlanabilir.
```js
const func = new Function("your function body");
const arr = new Array(arraySize);
....
new Object()
```
JavaScript'te `contructor` ile başlatmak için `new` sözcüğü kullanılır. Fakat bu yöntem tavsiye edilmez çünkü performansızdır. Örneğin, bir fonksiyonu `constructor` ile başlattığınızda, fonksiyonunuzu her çalıştırdığınızda, fonksiyonunuzun içeriği her defasında yeniden yorumlanır.