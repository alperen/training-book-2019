# JavaScript'te Memoization Fonksiyonu
Memoization fonksiyonları, hesaplaması maliyetli fonksiyonların daha önceki çıktılarını hafızasında tutarak fonksiyon hesaplama süresini ve bellek maliyetini düşürür. Örneğin bir fonksiyon belirli bir parametre ile çalıştırıldıkan sonra tekrar aynı parametreler ile çalıştırılırsa, ikinci çalışmasında birincidekine göre daha hızlı tepki verir çünkü bu değerler önbelleğe alınmıştır. Şimdi bu `memoization` fonksiyonunu JavaScript ile yazacağım.

```js
function memo(func) {
  const cache = {};

  return function(...params) {
    const stringifiedParams = JSON.stringify(params);
    const isExaminedBefore = cache.hasOwnProperty(stringifiedParams);

    if (isExaminedBefore) {
      return cache[stringifiedParams];
    }

    const result = func(...params);
    cache[stringifiedParams] = result;

    return result;
  };
}
```
`memo` adlı fonksiyonumuz, bir yüksek merteben fonksiyon. Bu fonksiyon, kendisine önce bir hedef fonksiyon alıyor. Daha sonra bu fonksiyonun parametrelerini her çağırıldığında alıp, daha önceki çalıştırmalardaki sonuçların tutulduğu `cache` objesinde olup olmadığını kontrol ediyor. Eğer varsa, sonuc `cache` objesinden alınıyor. Eğer yoksa, hedef fonksiyonda işlem yapılıp sonuc `cache` değişkeninde tutulmaya başlanıyor.

Kullanımı ise şöyle:
```js
const memoizedPower = memo(Math.pow);
console.log(memoizedPower(15, 15)); // calculated
console.log(memoizedPower(15, 15)); // from cache
```
Memoized fonksiyonlar, aynı parametre icin aynı sonuçu veren `pure function` fonksiyonlar için geçerlidir. Örneğin REST API isteği gibi. Şimdi `memoized` fonksiyonun sonucu ne kadar sürede ürettiğine bakacak olursak, fonksiyonu ilk kez çalıştırdığımızda hesaplaması 0.51 ms sürerken, ikinci çalıştırmada bu süre 0.19 ms'e düştü.
```js
console.time("calculate");
console.log(memoizedPower(15, 15));
console.timeEnd("calculate"); // 0.51ms
console.time("cache");
console.log(memoizedPower(15, 15));
console.timeEnd("cache"); // 0.19
```
