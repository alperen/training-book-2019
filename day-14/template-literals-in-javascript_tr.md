# Javascript'te Template Literal (Template Strings)
Javascript'te stringleri tanımlanın üç yolu var, bunlar herkesin bildiği `"yourString"`, `'yourString'` ve ES6 standartlarıyla gelen yeni yol:
> ` `templateString` `

Template stringler diğer string tanımlamalarına göre kaçış karakterlerine ihtiyac duymazlar içlerinde bir değişken veya fonksiyon gibi `computed-value` değerleri yorumlayabilir. Ayrıca `template-string` bir fonksiyona gönderilebilir.

Şimdi bir string tanımlanımın eski yolunu göstereceğim:

```js
const user = {
  name: "Alperen",
  age: 21
}
const awesomeString = "Hello," + user.name + "\nyou're " + user.age + " years old";

console.log(awesomeString)
/**
 * Hello, Alperen
 * you're 18 years old
 * /
```
Eski yöntemde, string parantezlerinin içine değişken yazamayız, string'leri bölüp daha sonra `+` işareti ile toplarız. Bunun yerine `template-string` kullanırsak:
```js
const awesomeString = `Hello, ${user.name}
you're ${user.age} years old.`;
```
`template-string` kullanarak hazırlanan değişkenimiz okuma bakımından daha kolay, hata yapma bakımından ise daha güvenlidir. `template-string` üzerinde `\n` gibi kaçış karakterlerini kullanmak zorunda değilsinizdir.

Ayrıca `template-string` ile yazdığınız string değerlerini fonksiyondan geçirebilirsiniz. Örneğin `getMarked` adında bir fonksiyonumuz olsun, bu fonksiyon aldığı stringdeki değişken kullanılan yerlerin arkasını sarıya boyasın. (`<mark />` kullanarak.)

```js
function getMarked(strings, ...variables) {
  let computedString = "";

  strings.forEach((string, index) => {
     computedString += `${string}${variables[index] ? `<mark>${variables[index]}</mark>` : ''}`;
  });

  return computedString;
}

const myAwesomeString = getMarked`Hello, ${user.name}. You're ${user.age} years old`;
```
`template-string` bir fonksiyona bağlanırsa `tagget-template-string` olarak adlandırılmaya başlar. Bu stringlerin fonksiyonlarının iki parametresi vardır, değişkene bağlı olmayan stringler (`strings`) ve değişkenler (`variables`). Biz bir döngüyle her stringi kendisinden sonraki `variable` ile eşleştirdik.