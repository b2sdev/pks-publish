
## What

- JavaScript library
    - HTML document traversal and maniupulation
    - event handling
    - animation
    - Ajax
        - simplifies JavaScript programming

## Function 사용법

```js
// [1] 
$(document).ready(function() {
	...
});
-> window.onload = function() {}과 같은 기능

// [2]
$(function() {
	...
});
-> 그냥 함수를 실행하라는 의미

// [3] 
(function($) {
	...
})(jQuery);
-> jQuery를 사용할 때 $의 의미를 jQuery에서 사용하겠다는 의미; 함수로 $를 매개변수로 넘기는 것.
```

## Etc
- 크롬 개발자모드 콘솔에서 jQuery 사용하는 방법
    - https://gomcine.tistory.com/entry/%ED%81%AC%EB%A1%AC-%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%AA%A8%EB%93%9C-%EC%BD%98%EC%86%94%EC%97%90%EC%84%9C-jQuery-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95