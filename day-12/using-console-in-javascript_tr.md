# JavaScript'te Console Sınıfını Kullanmak
JavaScript'te Console objesi, kullanıcılara daha kolay hata ayıklama yapabilmek için (`debugging`) çeşitli fonksiyonlar sunar. Bu fonksiyonlar, tarayıcının geliştiri araçlarındakı `Console` kısmına yazılırken, eğer `Node.js` gibi bir yazılımla JavaScript kodlarınızı çalıştırıyorsanız bu çıktıları terminalinizde görürsünüz. Temelde bir web sitesi üzerinde geliştirme yapmaya yarayan JavaScript'in Console objesi kullanıcı için vazgeçilmedir.
## Örnekler
Temelde, `Console` sekmemize bir veriyi yazdırmak istediğimizde `log` fonksiyonunu kullanırız. Console sınıfının `logging` fonksiyonları içerisinde aynı anda birden fazla veri yazılabilir, her türlü veri türü yer alabilir.
```js
console.log("Hello");
console.log(a) // Puts undefined on the screen if variable a is not defined.
console.log(a, b, c); // Puts values of a, b, c on a single line
console.log(userObj); // For an example: {name: "Alperen", age: 21}
console.log(null, undefined);
console.log(myAwesomeFunction); // Puts given function's body on the screen
console.log(myAwesomeFunction()) // Evaluates the function then puts it's returned value
```
Konsolda `logging` işleminde işleminde logunuzun tipini de `warning`, `info` veya `error` diye değiştirebiliriz, bu fonksiyonlar tıpkı `log` fonksiyonu gibi çalışır fakat `warning` için sarı, `info` için mavi ve `error` için kırmızı baskılama yaparlar.

`console.table` ise eğer içine bir obje veya dizi verirseniz, bunu bir tablo haline getirerek ekrana basar.
```js
console.table({
  user: "Alperen",
  age: 12
})
```
`console.count`, `console.time` fonksiyonları hata ayıklamayı kolaylaştırıcı console fonksiyonlarıdır, bu fonksiyonları çalıştırabilmek için bir etiket `label` ile çalıştırmak gerekir.

`console.count` fonksiyonu çalıştırıldığı her an kaçıncı defa çalıştırıldığını konsola yazar.
```js
function myAwesomeFunction() {
  console.count("myAwesomeFunctionCounter");
  // ....
}
myAwesomeFunction();
myAwesomeFunction();
myAwesomeFunction();
```
`console.time` fonksiyonu başladığı yerden bitirildiği yere kadar geçen süre farkını yazar, böylelikle fonksiyonumuzun veya kodumuzun ne kadar süre harcadığını görürürüz

```js
console.time("how long seconds myAwesomeFunction takes");
myAwesomeFunction();
console.endTime("how long seconds myAwesomeFunction takes") // 0.19ms
```