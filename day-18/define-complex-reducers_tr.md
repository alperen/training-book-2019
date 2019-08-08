# Karmaşık Reducer'lar Tanımlamak
Bir aksiyon tanımlanıp, `dispatch` yardımıyla çalıştırıldıktan sonra, Redux, bu işleme nasıl cevap verileceğini bilmek ister. Bunu yapmak `reducer` fonksiyonlarının görevidir. Reducer fonksiyonların argümanları `state` ve `action`'dır. Dispatch edilen actionlar payloadları ile birlikte gelir. Reducer fonksiyonlar, `side-effects` yani yan etkilere sahip olmayan `pure functions`'lardır. Örneğin bir reducer tanımlarsak,

```js
const defaultState = {
  login: false
};

const reducer = (state = defaultState, action) => {
  switch(action.type) {
    case "LOGIN":
      return {
        login: true,
      }
      break;
    case "LOGOUT":
      return {
        login: false,
      }
      break;
    default:
      return state;
  }
};

const store = Redux.createStore(reducer);

const loginUserAction = () => {
  return {
    type: "LOGIN"
  }
};

const logoutUserAction = () => {
  return {
    type: "LOGOUT"
  }
};

store.dispatch(loginUserAction()); // login: true

store.dispatch(logoutUserAction()); // login: false
```
Eğer `loginAction` `dispatch` edilirse, `reducer`'daki `switch-case` yapısı, `LOGIN` case'ine girer ve return edilen değer state'e geçirilir. İşlem, `dispatch` edildiği zaman, `store.getState` kontrol edilirse `login` state'inin `true`'ya eşit olduğunu görürürüz. Bu işlemler yardımıyla kullanıcının giriş yapıp yapmadığı durumunu state'te tutuyoruz.

## combineReducer kullanmak
`combineReducer` fonksiyonu bir store üzerinde birden fazla birbirinden ayrık state tutmamızı sağlar. Her bir state kendi `reducer` fonksiyonu ve aksiyonları ile birlikte gelmelidir. Reducer'ları ayırmak uygulamanızın daha kolay geliştirilmesinin önünü açar. `combineReducer` fonksiyonu birbirinden bağımsız `reducer` fonksiyonlarını birleştirir. Örneğin `authReducer` ve `counterReducer` 'ı aynı store üzerinde kullanmak istersek:
```js
const rootReducer = Redux.combineReducers({
  count: counterReducer,
  auth: authReducer
});
const store = Redux.createStore(rootReducer);
```