# Javascript'te Asenkron İşlem
Normalde bir progmanda code yazıldığı biçimde yukarıdan aşağıya işlenerek çalıştırılır. Bir çevrim anında yalnızca bir işlem yapılır. Bir fonksiyon çalıştırılır ve onun bitmesi beklenir. Eğer bitmesi beklenen fonksiyon başka fonksiyonlar da çağırıyorsa önce içerideki fonksiyonlar biter sonra dıştaki fonksiyon bitip başka bir göre geçilir. Ve bir çıktı oluşturulur. Asekron bir şekilde tasarlanmış programda fonksiyonun bitişini beklemenize gerek yoktur. Asenkron programlamanın temelinde bir iş yaparken başka şeyler yapmak mümkündür. Senkron programlamada aynı anda yalnızca bir iş yapılacağından, uzun süreli işleriniz gerçekleşirken kodunuzun çalıştırılması durdurulur. Buna `Blocking code` denir. Javascript'te asenkron programlama yapmak motorunuzun sağladığı api'ler sayesindedir.

## Promises
`Promise` objesi modern web tarayıcılarında asenkron fonksiyon yazmış için kullanılacak objedir. Çalıştırılması uzun süren işler (Bir resim çizmek, uzak sunucudan bilgi almak, bir dosyaya yazmak/ okumak gibi) bir `Promise` objesi döndürür. Böyle yapılacak işlem yapıldığı sırada, tarayıcıyı ya da kodun çalıştığı yeri bloklamaz. Uygulama kitlenmez. `Fetch`, uzak sunucudan bilgi almaya yarayan bir objedir, `Promise` döndürür.

```js
console.log("Started"); // 1
fetch("example.com").then((response) => {
  console.log("example.com gived a response."); // 3
}).catch((error) => {
  console.log("example.com gived an error response."); // 3
});
console.log("Ended"); // 2
```
Eğer `Promise` döndüren işlemler asenkron olmasaydı, senkron olsaydı, işlem başladığında bittiğini kesinlikle beklerdik fakat asenkron işlemde bu olmaz. Eğer log'ladığımız verinin sıralamasına bakarsak, `Promise` işlemi başladıktan sonra 2. log'un hemen çalıştırıldığını görürürüz. Bir `Promise` döndüren objenin iki adet fonksiyonu vardır. `then` ve `catch` fonksiyonları, asenkron işlemi kontrol etmek için kullanılan `callback` fonksiyonlarıdır. `then` fonksiyonu, yapılan işlem istenildiği gibi bir hata olmadan sonuçlandığında çalıştırılır. `catch` fonksiyonu ise bir hata oluştuğunda çalışır.

## await/async
`Await` sözcüğü asenkron fonksiyonlarda, `Promise` objelerinde, işlem bitene kadar kodu durdur anlamındaki sözcüktür. Bu anda işlem senkrona çevrilir, bitene kadar beklenir. `await` koyulmuş fonksiyonlarda `Promise` işleminin `then` fonksiyonunu direkt okuruz. Örneğin:

```js
const response = await fetch("example.com");
console.log(response) // example.com's gived a response.
```

## Async Fonksiyon
Eğer bir fonksiyonun içinde, `Promise` objesi kullanılıyorsa veya asenkron bir işlem yapılıyorsa bu fonksiyonun başına `async` sözcüğü eklenir. Asenkron fonksiyonlar, `AsyncFunction` objesinden türer örneğin:

```js
async function myAwesomeFunction(args) {
  return await anothermyAwesomeFunction();
}
async function hello() { return "Hello" };
let hello = async () => { return "Hello" };
```