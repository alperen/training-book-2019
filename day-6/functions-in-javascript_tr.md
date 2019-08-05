# Javascript'te Fonksiyonlar
Matematiksel olarak fonksiyonlar, bir kümedeki `x` değerini başka bir kümedeki `y` değerine eşler ve `y = f(x)` şeklinde gösterilir. Programlama da ise, fonksiyon, belirli bir işi yapmaya özelleştirilmiş kod parçacıklarıdır. Fonksiyonlar bir veya birden fazla kez çalıştırlabilirler.

## Function ve Procedure
Prosedürler, fonksiyonlar gibi belirli bir işi yapmak için özelliştirilmişlerdir fakat bir argüman almak zorunda değillerdir. Aynı zamanda bir değer de döndürmeyebilirler. Kendisine belirtilmiş bir görevi yapar ve durur. Fakat fonksiyonların bir girdisi ve çıktısı kesinlikle olmalıdır. Yeni bir şeyler üretmelidir.

## Fonksiyon Tanımlamak
Javascripte fonksiyonlar `first-citizen-function` özelliğine sahiptir. Bir isme sahip olabildikleri gibi, anonim de olabilirler.

```js
function calculateBirthYear(age) {
  return 2019 - age;
}

calculateBirthYear(19) // 2000;
```

Fonksiyon isimleri eğer varsa açıklayıcı olmalıdır.

```js
const getInitalsOfString = function (str) {
  return str.split(" ")
            .reduce(function (initialsOfString, word) {
              return `${initialsOfString} ${word[0]}`
            }, "")
            .trim();
}

getInitalsOfString("Alperen Turkoz") // A T
```

Yukarıdaki örnekteki fonksiyonlar anonim fonksiyonlardır ve anonim fonksiyonlar hangi değer atandıysa onun isimleriyle çağırılırlar.

## Arrow Function
Ayrıca fonksiyonların tanımlamak için kısa bir yöntem de `=>` sintaksını kullanarak bir `arrow-function` oluşturmaktır. Bu fonksiyonlar, `this`, `arguments`, `super` gibi sözcüklere sahip değillerdir ve anonimdirler.

Örneğin `getInitalsOfString` fonksiyonunu `arrow function` olarak kullanarak tanımlayalım:

```js
const getInitalsOfString = str => {
  return str.split(" ")
            .reduce(((initialsOfString, word) => `${initialsOfString} ${word[0]}`), "")
            .trim();
}

getInitalsOfString("Alperen Turkoz") // A T
```
Arrow fonksiyonlar, `return` sözcüğüne ihtiyac duymadan direkt olarak döndürür. Terminolojik ismi `lambda expression`'dur.