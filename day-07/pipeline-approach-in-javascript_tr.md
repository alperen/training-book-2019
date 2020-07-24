# JavaScript Pipe Line Yaklaşımı
Pipe line yaklaşımı, fonksiyonel programada kullanılan popüler bir yaklışımdır. Bu yaklaşım, bir verinin bir düzende birden fazla fonksiyonu dolaşması gerektiğinde kullanılır. Bir yazılım mimarisi olup kodun okunuşunu geliştirir. Aslında JavaScript'in yeni versiyonlarında pipe-line modeli desteklenmektir fakat bunu JavaScript ile  kendim tasarlayacağım:

Örneğin problemimiz bir dizindeki elemanlar için hakkında bu kurallar olsun:
* Elemanlar pozitif olmalı
* Her bir eleman en fazla bir kere dizide olmalı
* Elemanların küpü alınıp yeni bir dizi oluşturulmalı

Pipe yaklaşımı olmadan yaparsak:

```js
function selectPositives(array) {
  return array.filter(number => number > 0);
}

function getUniqueElements(array) {
  return array.reduce(function(arrayWithUniqueElements, number) {
    if (!arrayWithUniqueElements.includes(number)) {
      arrayWithUniqueElements.push(number);
    }

    return arrayWithUniqueElements;
  }, []);
}

function getCubesOfElements(array) {
  return array.map(number => Math.pow(number, 3));
}

const numbers = [42, 4, -5, -4, -16, 36, -22, -3, -5, 4, 28, 42, 36];

const newNumbers = getCubesOfElements(getUniqueElements(selectPositives(numbers)));

console.log(newNumbers); // [74088, 64, 46656, 21952]
```

Problemiz ve  fonksiyonlarımız doğru şekilde yapıldı. Görüldüğü gibi çok karmaşık olmayan bir yapıda dahil anlamada problem olabiliyor. İlk çalışacak fonksiyon sağ tarafta en sonuncusu ise en solda yazılmış. Bir fonksiyonda çıkan değer diğerine gidiyor. Bunun matematiksel ifadesi: `h(g(f(x))` şeklindedir.

`getCubesOfElements`, `getUniqueElements`, `selectPositives` fonksiyonlarının var olduğunu varsayarak, bunu pipe yakşalımı ile yaparsak:

```js
pipe = (functions) => (initialArgument) => functions.reduce((currentValue, func) => func(currentValue), initialArgument);
```

Bu yapıyı anlatacak olursam `reduce` fonksiyonu ile bütün fonksiyonları dolaşıp bir değer üretiyorum, bu ürettiğim değeri bir sonraki fonksiyona argüman olarak gönderiyorum. Başlangıç olarak da ilk veriyi set ediyorum. Eğer yukarıdaki problemi `pipe line` yaklaşımı ile çözersem şöyle gözükecek:

```js
const numbers = [42, 4, -5, -4, -16, 36, -22, -3, -5, 4, 28, 42, 36];
const newNumbers = pipe([
  selectPositives,
  getUniqueElements,
  getCubesOfElements
])(numbers) // [74088, 64, 46656, 21952]
```

Bu yaklaşımda, görev sıram ile fonksiyon sıram aynı, diğerindeki düzlük bana güçlük çıkarabilirdi. Yukarıda fonksiyondaları çalıştırmadan direkt olarak isimleriyle gönderdim, aslında `pipe` fonksiyonu, yüksek mertebeli fonksiyonlar için çok iyi ve kapsayıcı bir örnek. JavaScript'te fonksiyonlar, diziler, objeler bir başka yere referansla taşınırlar çünkü bu tipler primitif değildir.