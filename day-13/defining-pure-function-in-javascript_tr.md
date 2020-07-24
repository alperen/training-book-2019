# JavaScript'te Pure Fonksiyonlar Tanımlamak
Pure fonksiyonlar, aynı argümanlarla çalıştırıldığı taktirde sürekli aynı sonucu döndüren, deterministik yani aynı girdiler için farklı sonuçlar üretmeyen fonksiyonlardır. Pure fonksiyonlar üzerinde `side-effect` denilen fonksiyonlar kullanılmaz. Örneğin, pure fonksiyon üzerinde tarih-saat işlemi yapılmaz, girdi-çıktı işlemi yapılmaz, rastgele değer üretimi yapılmaz veya bir `API`'ye istek atılmaz. Çünkü `side-effect`ler fonksiyonun, deterministiğini bozar.

Örneğin:
```js
const double = x => x * 2;
console.log(double(5)); // 10
console.log(double(5)); // 10
```
`double` fonksiyonu bir pure fonksiyondur. Aynı argüman için sürekli aynı değeri döndürür. Çoğu matematiksel fonksiyon pure fonksiyondur. Örneğin bir fonksiyon, rassalığa, zamana vs bağlıysa, bu fonksiyonun `side-effect`'i vardır ve pure fonksiyon olarak adlandırılmaz. Bu tip fonksiyonlara `impure function` denir.
```js
const time = () => new Date().toLocaleTimeString();
time(); // 12:54:03
time(); // 15:54:04
```