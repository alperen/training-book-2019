# State Nasıl Oluşturulur
Redux'ta state'in tutulduğu fonksiyonlara `reducer` adı verilir. Her bir bağımsız state için bir reducer açılır. Örneğin: `userReducer`, `loadingReducer`, `projectReducer` gibi. Şimdi bir reducer tanımlayacağız. Her bir reducer varsayılan bir başlangıç state değeri ile gelmelidir ve reducer daima bir state objesi döndürmek zorundadır. Redux'ta state objenizi store'a taşımak için `createStore` fonksiyonuna gönderilir. Eğer birden fazla state kullanılacaksa `combineReducers` kullanılır.
## Store Oluşturmak
```js
const DEFAULT_STATE = 5;
const reducer = (state = DEFAULT_STATE) => {
  return state;
}

const store = Redux.createStore(reducer);
```
Uygulamamızın durumunu tutacak `store` değişkenine aktardık. Bu değişken `dispatch` fonksiyonlarını vs. döndürür. `store.getState()`, `state`'in son durumunu gösterir.
```js
const currentState = store.getState(); // 5
```

## Action Oluşturmak
Aksiyonlar, Redux'ta `state`'in yükseltimesi - değiştirilmes için özelleştirilmiş fonksiyonlardır. Bu fonksiyonlar, `dispatch`'e gönderilerek çalıştırılır. Örneğin bir aksiyon tanımlayalım. Temelde bu, bir obje döndüren fonksiyondur. Döndürülen obje direkt olarak `dispatch`'e de verilebilir. Aksiyonlar, yapılacak işlemi tanımlamalıdır. Örneğin: `createTaskCandidate`, `setSelectedCompany`, `getCurrentUser` gibi.
```js
const loginAction = () => ({
  type: "LOGIN"
});

store.dispatch(loginAction());
```