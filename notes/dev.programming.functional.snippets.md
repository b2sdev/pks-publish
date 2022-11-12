---
id: xjaqxo09yk7o1wq69amybai
title: Snippets
desc: ''
updated: 1668219094536
created: 1668218738780
---


Snippet

```js
{
    "user": "hughfdjackson",
    "posts": [
        { "title": "why curry?", "contents": "..." },
        { "title": "prototypes: the short(est possible) story", "contents": "..." }
    ]
}

var curry = require('curry')

// curry는 교재 p34, p129
// get :: String -> Object -> String
var get = R.curry((property, object) => object[property])
// map :: Function -> Object -> Object (?)
var map = R.curry((fn, value) => value.map(fn))

fetchFromServer()
	.then(JSON.parse)
	.then(get('posts'))
	.then(map(get('title'))


fetchFromServer()
.then(R.prop('posts'))
.then(R.map(R.props('title')))
.then(element => console.log(element))"
```

## dragons.js
```js
  "const R = require('ramda')
  
  let dragons = [
    { name: 'fluffykins', element: 'lightning'},
    { name: 'noomi',      element: 'lightning'},
    { name: 'karo',       element: 'fire'},
    { name: 'doomer',     element: 'timewarp'},
  ]
  
  // let hasElement = (element, obj) => obj.element === element
  // let lightDragons = dragons.filter(x => hasElement('lightning', x))
  
  // let hasElement = R.curry((element, obj) => obj.element === element)
  // let lightDragons = dragons.filter(hasElement('lightning'))
  
  let hasElement = R.propEq('element', 'lightning')
  let lightDragons = R.filter(hasElement, dragons)
  
  console.log(lightDragons)
```

## curry
```js
  getOnClick = (index) => (event) => message = buttons[index]
```

## 일급시민
```js
  const multiply = (x, y) => x + y;
  
  function add(x, y) {
  	return x + y;
  }
  
  const addAlias = add;
  
  const evens = [1, 2, 3].map(n => n * 2);
```

## closure
```js
  const add = x => y => x + y;
  
  function add(x) {
  	return function(y) {
  		return x + y;
  	};
  }
  
  // ----
  
  const createAdder = (x) => {
  	return (y) => x + y;
  };
  
  const add3 = createAdder(3);
  
  add3(2) === 5;
  add3(3) === 6;
  // closure는 이렇게 RECALL 가능
  
  // ----
  
  const request = (options) => {
  	return fetch(options.url, options)
  		.then(res => res.json());
  };
  
  const usersPromise = request({
  	url: '/users',
  	headers: { 'X-Custom': 'mykey' }
  });
  
  const tasksPromise = request({
  	url: '/tasks',
  	headers: { 'X-Custom': 'mykey' }
  });
  
  ==>
  
  const createRequester = (options) => {
  	return (otherOptions) => {
  		return request(Object.assign({}, options, otherOptions));
  	};
  };
  
  const customRequest = createRequester({
  	headers: { 'X-Custom': 'mykey' }
  });
  
  const usersPromise = customRequest({ url: '/users' };
  const tasksPromise = customRequest({ url: '/tasks' });
```

## partial application
```js
  const add = (x, y) => x + y;
  
  const add3 = partial(add, 3);
  
  add3(2) === 5;
  
  
  const request = (defaults, options) => {
  	options = Object.assign({}, defaults, options);
  
  	return fetch(options.url, options)
  		.then(res => res.json());
  };
  
  const customRequest = partial(request, {
  	headers: { 'X-Custom': 'mykey' }
  });
  
  const usersPromise = customRequest({ url: '/users' };
  const tasksPromise = customRequest({ url: '/tasks' });
```

## curry
```js
  const request = defaults => options => {
  	options = Object.assign({}, defaults, options);
  
  	return fetch(options.url, options)
  		.then(res => res.json());
  };
```

## Shoping Cart
```js
  const map = fn => arrray => array.map(fn);
  const multiply = x => y => x * y;
  const pluck = key => object => object[key];
  
  const discount = multiply(0.98);
  const tax = multiply(1.0925);
  
  const customRequest = request({
  	headers: { 'X-Custom': 'mykey' }
  });
  
  customRequest( { url: '/cart/items' })
  	.then(map(pluck('price')))
  	.then(map(discount))
  	.then(map(tax));
  
  customRequest( { url: 'cart/items' })
  	.then(map(compose(tax, discount, pluck('price')));
```

## Recursion
```js
  const factorial = (n) => {
  	if (n < 2) {
  		return 1;
  	}
  	
  	return n * factorial(n - 1);
  };
  
  OPTIMIZABLE
  
  const factorial = (n, accum = 1) => {
  	if (n < 2) {
  		return accum;
  	}
  
  	return factorial(n - 1, n * accum);
  };
  
  factorial(4);
  4 * factorial(3);
  4 * 3 * factorial(2);
  4 * 3 * 2 * factorial(1);
  4 * 3 * 2 * 1;
  4 * 3 * 2;
  4 * 6;
  24;
```

## curryRight
```js
  greaterThanOrEqual = (a, b) => a >= b
  const greaterThanOrEqualTo = _.curryRight(greaterThanOrEqual)
  
  let thirtyDaysAgo = (new Date()).getTime() - (86400000 * 30)
  const within30Days = greaterThanOrEqualTo(thirtyDaysAgo)
```

## Utils
```js
  const getTime = (dateString) => (new Date(dateString)).getTime()
  
  greaterThanOrEqual = (a, b) => a >= b
  const greaterThanOrEqualTo = _.curryRight(greaterThanOrEqual)
  
  let thirtyDaysAgo = (new Date()).getTime() - (86400000 * 30)
  const within30Days = greaterThanOrEqualTo(thirtyDaysAgo)
```

## Pure function
```js
  <참조 투명성>
  const add = (x, y) => x + y;
  
  add(2, 3) === 5;
  add(2, 3) === 5;
  add(2, 3) === 5;
  
  <IMPURE>
  let name = 'Jeremy';
  
  const getName = () => name;
  
  const setName = (newName) => {
  	name = newName;
  };
  
  const printUpperName = () => {
  	console.log(name.toUpperCase());
  };
  
  //----
  
  function doubleNumbers(numbers) {
  	const doubled = [];
  	const l = numbers.length;
  
  	for (let i = 0; i < l; i++) {
  		doubled.push(numbers[i] * 2);
  	)
  
  	return doubled;
  }
  
  doubledNumber([1, 2, 3]); // [2, 4, 6]
  
  // ----
  
  function doubleNumbers(numbers) {
  	return numbers.map(n => n * 2);
  }
  
  doubleNumbers([1, 2, 3]); // [2, 4, 6]
```

## Immutable
```js
  <MUTABLE>
  
  const hobbies = [
  	'programming',
  	'reading',
  	'music'
  ];
  
  const firstTwo = hobbies.splice(0, 2);
  
  console.log(firstTwo); // ['programming', 'reading']
  
  console.log(hobbies); // ['music']
  
  ==>
  
  const const hobbies = Object.freeze([
  	'programming',
  	'reading',
  	'music'
  ]);
  
  const firstTwo = hobbies.splice(0, 2); // TypeError
  
  // ----
  
  class Point {
  	constructor(x, y) {
  		this.x = x;
  		this.y = y;
  	}
  	
  	moveBy(dx, dy) {
  		this.x += dx;
  		this.y += dy;
  	}
  }
  
  const point = new Point(0, 0);
  
  point.moveBy(5, 5);
  point.move(-2, 2);
  
  console.log([point.x, point.y]); // [3, 7]
  
  ==>
  
  const createPoint = (x, y) => Object.freeze([x, y]);
  
  const movePointBy = ([x, y], dx, dy) => {
  	return Object.freeze([x + dx, y + dy]);
  };
  
  let point = createPoint(0, 0);
  
  point = movePointBy(point, 5, 5);
  point = movePointBy(point, -2, 2);
  
  console.log(point); [3, 7]
```
