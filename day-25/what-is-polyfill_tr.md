# Polyfill Nedir?
Polyfill web geliştirmede tarayıcının veya JavaScript motorunun desteklemediği API veya fonksiyonların desteklenmesini sağlayan üçüncü parti kod parçacıklarıdır. Bu kodlar, istenen fonksiyon tarayıcıda ya da motorda olmadığında, istenen fonksiyonun görevleri ile birebir yapacak bir fonksiyon yerleştirir. Yerleştirilen fonksiyonlar EcmaScript standartlarını okuyarak geliştirilir. Örneğin, Internet Explorer'ın eski sürümlerinde yeni API veya fonksiyonları kullanmak istiyorsunuz fakat bu API ve fonksiyonlar tanımlı değil. O zaman projenize ilgili polyfill'leri eklersiniz, eklemenizden sonra bu tarayıcıda istediğiniz fonksiyonlar tanımlanmış olur. Örneğin, `Math.floor` fonksiyonu tarayıcımızda olmamış olsun ve bunun polyfill'ini yazalım.
```js
if(!Math.floor) {
  Math.floor = function(number) {
    return !number && NaN || number - (number % 1);
  }
}

Math.floor(10.5);
```
`Math.floor` fonksiyonu verilen sayıyı kendine en yakın küçük tam sayıya yuvarlar. Bu kod parçasında ilk önce `Math.floor`'un `global scope` üzerinde var olup olmadığını kontrol ettik. Eğer yoksa, bunun  yerine geçecek bir fonksiyon ile fonksiyonu tanımladık.

Aynı bunda olduğu gibi başka büyük objeler üzerinde de polyfill yazılabilir. `Promise`, `Fetch` gibi objelerin polyfill'leri sıkça kullanılır. `@babel/polyfill` paketi bu polyfill fonksiyonlarını ve objelerin pek çoğunu içerir. JavaScript'in yeni versiyonlarında yazdığınız bir yazılımı daha düşük seviyeli JavaScript kullanan tarayıcı veya motorlarda kullanmanın bir yoludur.