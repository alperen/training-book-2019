# Eslint Nedir?
`Linter`, programlama dillerinde yazdığınız kod üzerindeki potansiyel bug'ları temizlemeye, kodları belirli bir düzene oturtmayı, kodlardaki gereksiz şeyleri kaldırmaya, kodunuzu analiz etmeye yarayan yazılımlardır. Her dil için özel olarak yazılır. `Eslint` ise JavaScript için yazılmış, özelleştirilebilir bir analiz programıdır. Eslint'e tanımlayacığınız kurallar veya daha önceden tanımlanmış paketleri kullanarak kodlarınızın bug'larını azaltabilir ve belirli bir standarta oturtarak takım içinde daha anlaşılabilir ve akıcı kodlar yazabilirisiniz. Eslint ile yazdığınız kodların, belirlediğiniz standartlara uygun olmadığında hata vermesini sağlarsınız. Şimdi bazı kuralları inceleyeceğim:

## Bazı Kurallar
Kurallar rastege seçilmiştir.

### no-magic-numbers
Bu kural matematiksel işlemlerde sabit değerlerin daha açıklayıcı olması için bu değerlerin birer sabit değişkene atanması gerektiğini söyler. Örneğin dakikadan saniyeye çeviren bir fonksiyonumuz olsun:

```js
const minutesToSeconds = (minutes) => minutes * 60;
```
Eğer doğru ayarları yapıp `no-magic-numbers` kuralını içeriye dahil edersek, `60` yazan yerde hata verecektir. Çünkü `60` bir `magic-number`'dır. Ne olduğu neye bağlı olduğu anlamsızdır. Bundan kurtulmak için kodu daha açıklayıcı yazarız:
```js
const SECONDS_IN_A_MINUTE = 60;
const minutesToSeconds = (minutes) => minutes * SECONDS_IN_A_MINUTE;
```

### no-new-object
Bu kural `new Object` sintaksını kabul etmez.
```js
const o1 = new Object(); // bad
const o2 = {}; // good
```

### no-unused-vars
Bu kural oluşturulup kullanılmayan değişkenleri kaldırmaya yönelik kuraldır.

Bunun gibi eslint kuralları, takımınızın veya kişisel tercihlerinizin doğrultusunda bir eslint konfigürasyon dosyasına yazılır. Yazılan bu kurallar, kodunuzun daha az hataya sahip olmasına olanak sağlar. Bazı hataları önceden yok etmenize yardımcı olur. Daha yüksek sertliğe sahip kurallar kümesi daha düzgün kod yazmak için bir neden olabilir. Kurallar kümesini kendinizin tanımlayıp başkalarıyla paylaşabileceğiniz gibi başkalarından alabilirsiniz. Google veya Airbnb gibi popüler şirketler kurallarını paylaşmışlardır. Popüler eslint kurallarını kullanmak kodunuzun `Best Practices` yani en iyi uygulamalar trendini takip etmesini sağlar. Kod tasarlama ve okunabilir kod yazma kalitenizi arttırır.