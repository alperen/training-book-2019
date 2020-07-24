# JavaScript'te Obje Kalıtımı
JavaScript'te bir objeden diğer bir objeye `inheritance` yani kalıtım yapmak için objelerin prototiplerini birbirine eşitleriz. Örneğin, `Bird` objesini, `Animal` objesinden kalıtalım. JavaScript'te bir objenin prototip verisini `reassign` ederken, `constructor` propertisini bizim `constructor function`'ımıza eşitlemeliyiz.

```js
function Animal{}
Animal.prototype = {
  constructor: Animal,
  eat: () => {
    console.log("I'm eating something");
  }
}

function Bird() { }
Bird.prototype = Object.create(Animal.prototype);
Bird.prototype.constructor = Bird;

Bird.eat(); // I'm eating something
```
`Object.create`, kendisine verilen bir objeden yeni bir obje üretir. Aslında, olması gerektiği gibi kopyalar. Biz ürettiğimiz objeyi, `Bird` fonksiyonumuzun prototipine eşitledik. Daha sonra `Bird` objesinin `constructor`'unu yine `Bird`'e. Bunu yapmasaydık, `Bird` objesinin `constructor`'u `Animal` fonksiyonunu gösterirdi.