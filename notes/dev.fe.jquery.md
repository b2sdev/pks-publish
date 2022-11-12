---
id: wejk9lrgygrtmaeoehqho8a
title: jQuery
desc: ''
updated: 1668223778283
created: 1495350383000
---

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