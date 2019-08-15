# Getter ve Setter Fonksiyonlar
Getter ve Setter fonksiyonlar, OOP'de `Encapsulation` yapmak için kullanılan bir fonksiyon biçimidir.

## Getter Fonksiyon
Bazen bir veriye erişmeden önce o veriyi inceleyip, üzerinde işlemler yapmak gerekebilir. Getter fonksiyonlar bunu daha açıkça yapabilmemize olanak sağlar. Örneğin bir objenin `log` niteliğinde bir dizide belirli değerler tutalım, `latest` niteliği bu dizinin son elemanını göndersin. Bunu fonksiyonu `get` cümlesiyle tanımlayalım:

```js
var obj = {
  log: ['a', 'b', 'c'],
  get latest() {
    const count = this.log.length;
    if (count == 0) {
      return undefined;
    }
    return this.log[count - 1];
  }
}
console.log(obj.latest); // c
```

Eğer dizide hiç bir eleman yoksa, son eleman zaten tanımlanmamış olur (`undefined`). Diğer türlü dizinin son elemanını `return` ettik. Getter fonksiyonlar kesinlikle bir değer döndürmelidir (`eslint-getter-return`). Getter fonksiyonlar, çalıştırılmaları için fonksiyon parantezlerine ihtiyaç duymazlar `obj.latest()` gibi. Bir nitelik gibi çağrılırlar. Bir `computed-value` üretirler.

## Setter Fonksiyon
Setter fonksiyon, çağırıldığında yapılacak bir `set` işlemini kontrol etmemize yarayan fonksiyon türleridir. Bu fonksiyonların başına `set` sözcüğü eklenir. Setter fonksiyonlar bir değer döndürmezler. Bu fonksiyonlar, eşitlenmesi istenen verinin okunabilmesi için bir parametre alırlar. Yukarıdaki `latest` fonksiyonunun setter halini yazarsak:

```js
var obj = {
  log: ['a', 'b', 'c'],
  set latest(value) {
    this.log.push(value);
  }
}

obj.latest = "X";
console.log(obj.latest); // X
```

Getter fonksiyonlarında olduğu gibi setter fonksiyonlarında da fonksiyon `()` işaretlerine ihtiyaç duymaz. Ayrıca `setter` fonksiyonlarının çalışması için bir eşitlemeye ihtiyaç vardır (`=`). Bu eşitlemenin sağ tarafındaki değer, sol taraftaki fonksiyona parametre olarak aktarılır (`value`).