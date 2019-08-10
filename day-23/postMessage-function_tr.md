# Javascript İle Başka Bir Sekmeye (Pencereye) Mesaj Göndermek
`window.postMessage` fonksiyonu iki sekme veya iki pencere arasında bir veri göndermenin güvenli yoludur. Bu fonksiyon sayesinde hedef pencereler birbirlerine mesaj, sinyal, veri gibi belirlenmiş bilgiler göndererek iletişim kurabilirler. Veri gönderim işlemi, iki sayfa arasında, bir sayfanın açtığı popup ile sayfa arasında ve bir sayfa içindeki `iframe` etiketine etki eder.

Ben Hipo'da bunu, bir sayfanın açtığı popup penceresini kapatmak için kullandım. Temelde `window.close` fonksiyonu o anda bulunan pencereyi kapatabilir. Fakat kullanıcı güvenliği sebebiyle, javascript'te hiç bir sekme kendini kapatamaz. Kapatmaya çalıştığında `Scripts may close only the windows that were opened by it.` uyarısını alırız. Bunu çözebilmek için açılan pencereden (popup), açan pencereye önce bir kapatma sinyali gönderdim. (`POPUP_CLOSE_SIGNAL`) daha sonra açan pencereye gelen bütün mesajları okuyup benim istediğim sinyalin gelmesini bekledim. Doğru sinyal geldiğinde, popup penceresini kapatacak işlemler yaptım. Çünkü, pencereler kendini kapatamaz fakat bir pencere açan pencere, açtığı pencereyi kapatabilir.

`window.postMessage` kullanarak her türlü veri gönderilebilir. Gönderilen verinin bir string biçiminde işlenmesi gerekmez çünkü veriler güvenli bir şekilde gönderilebilmesi için `The structured clone algorithm` algoritması ile işlenir. Parametre şeklinde verilen bilginin kendisi değil bir kopyası gönderilir.

Bir sayfaya gönderilen mesajları dinlemek için aşağıdaki gibi bir fonksiyon tanımlanmalıdır.

```js
function receiveMessage({data, origin}) {
  console.log(data)
}

window.addEventListener("message", receiveMessage, false);
```

Bu fonksiyonun ilk parametesi `event`'i destruct edip içinden `data` ve `origin` değişkenlerini aldım. Gönderilen her verinin bir `data` bir de nereden geldiğini anlatan `origin` verisi vardır.
Örneğin bu fonksiyonu alt taraftaki penceremize tanımlamış olalım. Popup'tan aşağıya (açan pencereye) veri göndermek için:

```js
window.opener.postMessage("POPUP_CLOSE_SIGNAL");
```
İşlemini yaparız. Popup pencereler, başka bir pencereden üretildiğinden bir `opener` penceresi vardır. `opener` değişkeni açan pencereyi referans eder. O zaman, sinyali aldığımızda kapama işlemi yapacağımız için dinleyici fonksiyonunu bu şekilde düzenleriz:

```js
const popup = window.open("popup.html");

function receiveMessage({data, origin}) {
  if (data === "POPUP_CLOSE_SIGNAL") {
    popup.close();
  }
}
```
