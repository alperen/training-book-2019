# Javascript'te Yıkarak Eşitleme
Yıkarak eşitleme `Destructuring Assignment`, Javascript'te bir arrayın elemanları veya bir objenin öznitelikleri için yapılan, bu verileri ayrık bir biçimde yazmamızı sağlayan bir sintakstır. ES6 ile gelen bir özelliktir.

## Örnekler

### Bir diziyi yıkmak
Eğer Javascript'te bu tip bir özellik olmasaydı ve bir dizinin ilk üç elemanını ayrık bir değişkene almak isteseydik şu şekilde yapardık:
```js
const numbers = [5, 6, 7, 8, 9, 10];
const first = numbers[0]; // 5
const second = numbers[1]; // 6
const third = numbers[2]; // 7
```
Bu yol uzun ve pek estetik değil, yıkarak eşitlemeyi kullanarak aynı kodu bu şekilde yazarız:
```js
const numbers = [5, 6, 7, 8, 9, 10];
const [first, second, third] = numbers;
console.log(first); // 5
console.log(second); // 6
console.log(third); // 7
```
Yukarıdaki örnekte yazıldığı gibi bir sintaksa sahipsek, eşitlemenin sol tarafındaki değişken isimleri yazılış sırasıyla dizideki elemanları alır. Örneğin ikinci elemanı veya başka bir elemanı almak istemiyorsak aralarına yalnızca `,` işareti koyarız.
```js
const [first,,third,,sixth] = numbers;
console.log(sixth); // 10
```
Javascript'te bir veriyi yıkarken eğer yıktığınız veri `undefined` döndürüyorsa bu veriye bir varsayılan değer atayabilirsiniz.
```js
const numbers = [2, undefined, 5];
const [
  first,
  second = "NOT_DEFINED",
  third = "NOT_DEFINED",
  fourth = "NOT_DEFINED"
] = numbers;
console.log(second) // NOT_DEFINED
console.log(third) // 5
console.log(fourth) // NOT_DEFINED
```
Bu örnekte üç elemanlı dizinin ikinci elemanı var fakat `undefined` döndürmüş. `undefined` döndürebileceği düşünülen her yıkım değişkenine varsayılan bir değer atanabilir. Aynı zamanda üç elemanlı bir dizide dördüncü elemanı okumaya çalıştık. Bu javascript'te `undefined` döndürmeye sebep olur. Yalnızca yıkılan değişken `undefined` ise ona bir varsayılan değer atayabiliriz. `null` değişkenler, tanımlıdır ama içleri boştur.

### Swap İşlemi
İki değişkenin değerlerini birbiri ile değiştirmek için yapılan işleme `swap` işlemi denir. Bu işlemi yapabilmek için üçüncü bir değişkene de ihtiyac vardır. Fakat Javascript'te buna ihtiyaç duymazsınız, destructing işlemi ile bunu çözebilirsiniz.
Destructing olmadan:

```js
let a = 15;
let b = 25;
const temp = a;
a = b;
b = temp;
```
Fakat destructing ile yapmak daha kolay ve anlaşılabilirdir.
```js
let a = 15;
let b = 25;
[a, b] = [b, a];
console.log(a) //  25
console.log(b) // 15
```
### Objeleri Yıkmak
Objeler de aynı diziler gibi yıkılabilir. Örneğin bunu yıkım sintaksını kullanmadan yazarsak:
```js
const user = {
  name: "Alperen",
  age: 21
};
const name = user.name; // Alperen
const age = user.age; // 21
```
Aynı işlemi destructing ile yaparsak:
```js
const {
  name,
  age,
  surname = "Surname is not defined",
} = user;

console.log(name) // Alperen
console.log(age) // 21
console.log(surname) // Surname is not defined
```
Tanımlanmamış `undefined` nitelikleri yıkmak istediğimizde, onlara bir varsayılan değer atayabiliriz. Yıkmak istediğimiz nitelikler, yıkılacak değişkende bulunmak zorundadır ve doğru bir key eşleşmesi ile onları çağırmalırsınız. Eğer yıkmak istediğiniz değişkenin ismini değiştirmek istiyorsanız, aşağıdaki gibi yazmalısınız:
```js
const {
  user: username,
  age: userage
} = user;
console.log(user) // undefined
console.log(username) // Alperen
```
Yukarıdaki örnekte görüldüğü gibi değişkeni `user` olarak değil `username` olarak aldık.

### Resting
`Resting`, bir yıkımda arda kalan elemanları almak için kullanılır örneğin, bir diziyi yıkalım:
```js
const numbers = [5, 6, 7, 8, 9, 10];
const [first, second, ...remainingNumbers] = numbers;
console.log(first) // 5
console.log(second) // 6
console.log(remainingNumbers) // [7, 8, 9, 10]
```
`Resting` işlemi `...` sintaksı ile yapılıyor. Arda kalan sayılar `remainingNumbers`, `first` ve `second` değişkenin değerlerini içermiyor. Aynı zamanda objeler de rest işlemine tutulabilir

### Shorthand Yöntemi İle Obje Tanımlamak
Javascript'te değişkenlerinizi kullanarak objeler yaratabilirsiniz. Eğer değişkenlerinizin adları ile objenizdeki anahtar `key` değerleri aynı olacaksa bunlara, bir değer `value` belirtmeniz gerekmez. Buna `Shorthand` yöntemi denir. Örneğin eğer bu yöntem olmasaydı:

```js
const name = "Alperen";
const age = 21;
const surname = "Turkoz";

const user = {
  "name": name,
  "age": age,
  "surname": surname
}
console.log(user.name) // Alperen
```
Fakat bunu short hand yöntemi ile yaparsak:
```js
const name = "Alperen";
const age = 21;
const surname = "Turkoz";

const user = {
  name,
  age,
  surname
}
console.log(user.name) // Alperen
```
Bu daha anlaşılabilir bir yöntemdir ve daha kolaydır.
