# Javascript'te Küme İşlemleri
Javascript'te Set objesini kullanarak iki küme arasındaki bazı işlemleri yapan fonksiyonları bu şekilde tanımlayabiliriz, örnek kümelerimiz bunlar olsun:

```js
var setA = new Set([1, 2, 3, 4]),
    setB = new Set([3, 4, 5, 6]);
```

## Kesişim (Intersection)
İki küme arasındaki ortak elemanlarından yeni bir küme oluşturur.

```js
function intersection(firstSet, secondSet) {
  const intersection = new Set();

  for (var element of secondSet) {
    if (firstSet.has(element)) {
      intersection.add(element);
    }
  }

  return intersection;
}

intersection(setA, setB); // => Set [3, 4]
```

## Birleşim (Union)
İki kümelerin bütün elemanlarını birleştirir. Ortak elemanları en fazla bir kere yazar.

```js
function union(firstSet, secondSet) {
  var union = new Set(firstSet);

  for (var element of secondSet) {
    union.add(element);
  }

  return union;
}

union(setA, setB); // => Set [1, 2, 3, 4, 5, 6]
```
Bu fonksiyonda, birinci parametreden yeni bir küme oluşturduk. Bu kümeye birinci kümedeki bütün elemanları almış olduk. Daha sonra ikinci kümeden de elemanları alıp birleşime ekledik. Verinin tekrar edip etmediğini kontrol etmeyiz çünkü, `Set` objesi bunu bizim yerimize yapar.

## Fark (Difference)
İki küme arasında ortak olmayan elemanları alır. Bu fonksiyon `firstSet \ secondSet` işlemini yapar, yani, `firstSet`'ta olup `secondSet`'te olmayan elemanlar şeçilecek.

```js
function difference(firstSet, secondSet) {
  var difference = new Set(firstSet);
  for (var element of secondSet) {
      difference.delete(element);
  }
  return difference;
}

difference(setA, setB); // => Set [1, 2]
```