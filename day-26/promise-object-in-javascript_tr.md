# Promise Objesi
`Promise` objesi, eşzamansız veya yapması ertelenmiş işlemler için kullanılır. Promise objeleri, işin henüz tamamlanmamış ama ileride tamamlanabileceğini gösterir.

## Terimler
Bir `Promise`'ın hangi durumda olduğunu anlamak için bazı terimler kullanırız.

* Pending: Henüz işlem yapılıyorken, bir cevap verilmemişken.
* Fulfilled: İşlemin başarıyla bitirildiğinde.
* Rejected: İşlemin başarısız bitirildiğinde.
* Settled: İşlemin fulfilled veya rejected durumunda olup, pending olmadığı durumlarda.
* catch(): İşlem başarısız bitirildiğinde çalışan fonksiyon.
* then(): İşlem başarılı bitirildiğinde çalışan fonksiyon.
* finally(): İşlemin her durumunda çalışan fonksiyon.

## Bir Promise Objesi Oluşturmak
Bir `Promise` objesi işlemin yapılacağı fonksiyonu parametre olarak alır. Bu fonksiyonun `resolve` ve `reject` adında iki `callback` fonksiyonu vardır. Bu fonksiyonlar işlem durumuna göre çalıştırılmalıdır. Eğer çalışmazsa, `Promise`, `pending` durumunda kalır. Eğer işlem bittiyse `resolve`, bir hata varsa `reject` fonksiyonunu çalıştırırız. Bu fonksiyonlara verilen parametreler direk olarak aktarılır.

```js
async function awesomeAsyncFunction() {
  return new Promise((resolve, reject) => {
    // function body
    resolve("Promise resolved.");
  });
}
```

Yapılan uzun işlemler sonucunda eğer işlem başarısızsa `reject` fonksiyonunu çalıştırırız. Örneğin, uzak sunucuya bağlanayamadığımızda veya bir dosyaya veri yazamadığımızda. Örneğin bunu çalıştırılaım:

```js
awesomeAsyncFunction().then((response) => {
  console.log(response); // Promise Resolved.
}).catch((error) => {
  console.error(error);
}).finally(() => {
  console.log("This works always.");
})
```