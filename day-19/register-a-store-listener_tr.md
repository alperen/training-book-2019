# Bir Store Dinleyici Fonksiyonu Tanımlamak
Store'unuzda bir değişiklik olduğunu, bir aksiyon dispatch edildiğini anlamanın bir yolu, store'unuza bir dinleyici fonksiyon tanımlamaktır. Bu fonksiyon sayesinde store'unuzdaki değişikleri görebilirisiniz. Örneğin, bir `addAction` diye bir fonksiyonunuz olsun. Bu fonksiyon state'inizdeki bir sayıyı her çalıştığında bir arttırsın. Bunu takip etmeye çalışalım:

```js
let count = 0;
store.subscribe(function() {
  console.log("State has changed");

  const currentState = store.getState();

  count = currentState;
});
store.dispatch(addAction()); // 1
console.log(count); // 1
store.dispatch(addAction()); // 2
console.log(count); // 2
store.dispatch(addAction()); // 2
console.log(count3); // 1
```
Bu şekilde store'a abone olarak, store üzerindeki değişiklikleri görebiliriz.