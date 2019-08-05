# Javascript'te Ön Tanımlı Gelen Yüksek Mertebeli Fonksiyonlar
Javascript dili ile birlikte gelen bazı yüksek mertebeli fonksiyonlar: `forEach`, `map` ve `reduce` fonksiyonlarıdır. Bu fonksiyonların hepsi array'ler üzerinde çalışır.

## forEach fonksiyonu
Bu fonksiyon, bir fonksiyondaki bütün elemanları dönen ve geriye bir değer döndürmeyen fonksiyondur.
Örneğin:

```js
const ages = [10, 15, 25, 35];

ages.forEach(function (age) {
	console.log(age); // Puts the screen each age. Age is element of ages array.
});
```

## map Fonksiyonu
Bu fonksiyon, bir dizinin bütün elemanı döner, geriye bir değer bekler. Geri döndürülen değer ile dizinin o anki elemanın değerini değiştirir.

```js
const ages = [10, 15, 25, 35];

const birthYearsOfAge = ages.map(function(age) {
	return 2019 - age;
});

console.log(birthYearsOfAge); // Puts an array which contains 2009, 2004, 1994, 1984
```

## reduce Fonksiyonu
Reduce fonksiyonu, akümülatör sahip bir fonksiyondur. Bütün elemanları dolaşır, bir değer bekler. Fakat döndürdüğünüz değer, `map` fonksiyonundaki gibi bir diziye değil, akümülatör değişkenine etki eder. Reduce fonksiyonun sintaksı:
`array.reduce((accumulator, currentValue, array), initialValueOfAccumulator)`

Örneğin:
```js
const ages = [10, 15, 25, 35];

const totalOfAges = ages.reduce(function(accumulator, age) {
	return accumulator + age;
}, 0);

console.log(totalOfAges); // Puts 85 on the screen.
```