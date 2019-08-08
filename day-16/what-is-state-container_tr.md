# State Container'ı Nedir?
Eğer web sitesinizi `Single Page Application` metodolojisini kullanıyorsanız, bazı kaynaklarınız tektir. Örneğin, web sitenizde yalnızca bir `html` dosyası vardır ve kullanıcının isteği sayfayı javascript ile yöneterek, dinamik olarak oluşturursunuz. Bu tip bir yöntemde, web sitesinin o anki durumunu, bilgilerini tutmanız gerekir. Bu bilgilerin bulunduğu yapıya `State Container` denir. Bu yapı içerisinde, kullanıcının bilgileri, kullanıcının veritabanınıza kaydettiği bilgiler,uygulamanızın o anki durumu, lokasyon gibi pek çok bilgi bulunur. Kısaca `state container`, uygulamanızın kullanıcı tarafındaki veritabanıdır. `State Container`, `SPA` ile yapılmış websitelerinde, verinin taşınması için de kullanılır. Örneğin, kullanıcının açtığı konu başlıklarını state'inize kaydedip, ihtiyacınız olduğunuzda kullanabilir veya değiştirebilirsiniz. Eğer bir `state-container`ınız olmasaydı, ihtiyacınız olan bilgiyi her seferinde tekrar sunucunuzdan istemek iserdiniz. `State Container`, uygulamanızın durumunu tutar ve onun direkt olarak değiştirilmesini engeller, kullanıcı tarafında yaptığınız bir veri yapısıdır. `State`, kullanıcın tarayıcısında olduğundan dolayı sayfa kapatıldığında yok olur. `State` tutma işleminde, `Single Source of Truth` konsepti uygulanılır. Bu konsept, verinin tek bir kaynaktan doğup, tek bir kaynağa yazılacağını garanti altına alır. Aynı veri uygulamanın başka bir yerinde tutulamaz, tekrar edilemez. Bir verinin birden fazla yerde tutulması, verimi azaltır. Çünkü eğer veri değişirse diğer yerleri de değiştirmeniz gerekir. Bazı izleyici fonksiyonlar yardımıyla, uygulama `state`ini değiştirdiğinizde arayüzünüzü de değiştirebilirisiniz. Uygulama bir veri katmanı eklemek, işlerinizi hafifletecektir.

## Terminoloji
### Action
`State Container` elle değiştirilemez, `immutable` bir objedir. Değiştirilmesi için anlamlı fonksiyonlara ihtiyaç duyar bu fonksiyonlar `action` olarak adlandırılır.  Bu fonksiyonlar, bir değere ihtiyac duyabilir. `payload`. `State`'in elle değiştirilememesi, bunun bir fonksiyon ile değiştirilmesi verinin doğrulunu bozmayı engeller. Fonksiyon temelli bir state değiştirme işleminde işlemin ne zaman nerede yapıldığını takip edebilirsiniz.
Örneğin:
```js
createUserAction(payload);
setAuthenticatedUser({
	name: "Alperen",
	age: 21
});
getUserData();
addBlogPostToCategory(blogPayload, categoryId);
```
### Dispatch
Dispatch, state'in üzerinde daha global bir fonksiyondur. Verinin akışını kontrol eder. Bu fonksiyon, bir parametre olarak `action` alır. Temelde, `action`lar çalıştıktan sonra `state`'in değiştirilmesi için gerekli işlemleri yapar.
```js
dispatch(setAuthenticatedUser({
	name: "Alperen",
	age: 21
})); // Authenticated user reduced into payload.
```
### Reducer
Her action bir sabit (`constant`) değer ile gelir. Ve her action için bu farklı olmalıdır. Reducer'ın görevi gelen sabite göre payload ile state arasındaki doğru işlemi yapmaktır. Dispatch, `reducer`'ı çalıştırır. Çıkış noktası `Array.reduce`'tır. Burada akümülatör, uygulamanın `state`tidir.