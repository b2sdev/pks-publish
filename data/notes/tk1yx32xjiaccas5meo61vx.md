
- React로 Angular의 Tour of Heroes 개발
    - https://github.com/coryhouse/react-tour-of-heroes/

- 리액트 네이티브로 안드로이드 앱 개발하기의 장단점
    - https://academy.realm.io/kr/posts/react-native-android-pros-cons/


```js
const myData = [].concat(this.state.data)
	.sort((a, b) => a.item > b.item)
	.map((item, i) => 
		<div key={i}> {item.id} {item.time}{item.description}</div>
)
```