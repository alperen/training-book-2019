# Yüksek Mertebeli Fonksiyon
Fonksiyonlar, yazılım dillerinin vazgeçilmez aletleridir. Bir fonksiyon tasarım yaklaşımı olan, `Higher Order Function` (Yüksek Mertebeli Fonksiyon) tipi fonksiyonlar, bir argümanı fonksiyon ya da sonucunda fonksiyon döndüren tipteki fonksiyonlardır. Go, JavaScript, Haskell gibi pek çok dilde tanımlanabilir. Temelde, bu bir matematiksel yaklaşımdır. Fonksiyonel programlamanın bir parçasıdır.

Standart fonksiyonlar, argüman olarak primitif veri tipleri alıp, bunları döndürürken, yüksek mertebeli fonksiyonlarda bu bir fonksiyon olabilir. Bu fonksiyonların matematiksel `Currying` olarak modellemesi `f(g(x))` şeklindedir. Örneğin bu fonksiyonun çıktısı `y` değişkenine eşit olsun. `->` sembolü, bir `x` değişkeninin hangi fonksiyonlardan geçtiğini göstersin, `y` değişkenine aşağıdaki gibi ulaşırız:
`x -> g(x) -> f(x) -> y`

## Örnekler

### Fonksiyon Olarak Argüman

```js

function multipleWithTwo(number) {
	console.log(number * 2);
}

function repeat(n, action) {
	for(let i = 0; i < n; i++) {
		action(n);
	}
}

repeat(3, multipleWithTwo);
```

Bu örnekte, `n` bir sayıdır. Örneğin, 3 verildiğinde döngü 3 kere döner. Hem bir döngü çevriminde, o anki sayı fonksiyon olan, `action` argümanına gönderilir. Örnekte, `action` argümanı `multipleWithTwo` fonksiyonu olarak belirlenmiştir. `multipleWithTwo` fonksiyonu her bir sayı için çalışır.

### Geri Dönüş Değeri Olarak Bir Fonksiyon
```js
function exponentFactory(base) {
	return function(exponent) {
		return Math.pow(base, exponent);
	}
}

const exponentsOfTwo = exponentFactory(2);
const exponentsOfFour = exponentFactory(4);

console.log(exponentsOfTwo(3)) // 2^3 = 8
console.log(exponentsOfTwo(4)) // 2^4 = 16
console.log(exponentsOfFour(1)) // 4^1 = 4
console.log(exponentsOfFour(4)) // 4^1 = 256
console.log(exponentFactory(10)(2)) // 10^2 = 100
```
Bu örnekte, `exponentFactory` fonksiyonu bir `base` argümanı ile çağırıldığında yeni bir fonksiyon dönürür, bu döndürülen fonksiyon bir `exponent` değeri alır. Bu fonksiyonu da çalıştırıldığında da matematiksel olarak `baseᵉˣᵖᵒⁿᵉⁿᵗ` işlemi yapılır. Yani, bir değişken olarak `exponentsOfTwo`, bir fonksiyonu gösterir.