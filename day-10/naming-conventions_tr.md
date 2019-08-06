# İsimlendirme Düzenleri
Yazılımların mimari aşamasında alınmış kararlar, projelere başka kişiler tarafından okunma ve katkı sağlama yeteneklerini arttırır. İsimlendirme düzenlemeleri projelerin daha istikrarlı bir şekilde gelişmesine yardım eder. Bu seçimler tamamen ekibin şahsi kararlarına bağlı olmakla birlikte, dünya genelindeki genel kabulün de göz önünde bulundurulması, ekibe yeni biri geldiğinde ona yardımcı olur.

## Değişken Yazma Biçimleri

### Pascal Case
`Pascal Case` tipi adlandırma sınıf yapılarını tanımlamada kullanılır. Yalnızca sözcüklerin ilk harfleri büyüktür. Ayrıca sınıfların isimleri, dosya isimleri ile aynı olmalıdır:
```js
// EmailService.js
class EmailService extends ApiFactory {
  //....
}
```

### Camel Case
`Camel Case` yalnızca ilk sözcüğün ilk harfinin küçük, diğer sözcüklerin ilk harfleri büyüktür. Değeri sabit olmayan değişkenlerin adlandırmasında ve fonksiyonlarda kullanılır:
```js
const usersName = [];
const currentProject = {
  color: "black",
  isActive: true,
  isArchived: false
}
const projectsList = [];

function generatePopupParams(params, junctionCharacter = ",") {

}
```
`Boolean` değer tutan değişkenler isimlendirilirken, İngilizce'deki söylendiği gibi yazılır. Çünkü bu değişkenleri işleme soktuğumuzda okunuşu kolaylaşır: `if (hasUserDebitCard)`

### Snake Case (All Capsed)
`Snack Case` kelimelerin arasında `_` koyularak yapılan isimlendirme yöntemidir. `All Capsed` bütün harflerin büyük olduğunu gösterir. Sabit değere sahip değişkenler için kullanılır:
```js
const PI = 3.14;
const TL_CURRENCY = 6.00;
const USER_MINIMUM_AGE = 18;
const MAXIMUM_MARGIN_OF_ERROR = 0.10;
```
Proje içerisindeki bu sabitler projenin birden fazla yerinde kullanılmak üzere tasarlanmıştır. Açıklayıcı olmalı ve her yerden ulaşılabilir olmalıdır. Proje üzerinde sabitler tanımlamak, bir değişiklik gerektiğinde yapmamız gereken iş yükünü azaltır. Daha açıklayıcıdır.

### Kebab Case
`Kebab Case`, tüm harflerin küçük olduğu ve bu kelimelerin `-` işaretiyle birleştirildiği isimlendirme türüdür. Bir değişken tanımlama kurallarına uymaz, dosya isimlendirmesinde kullanılabilir.