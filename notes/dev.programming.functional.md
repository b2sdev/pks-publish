---
id: 0dgdfinbj1n0ojsgy5glg9w
title: Functional Programming
desc: ''
updated: 1668238458749
created: 1530669965000
---


## 특징

- PURE
- DECLARATIVE
  - DECLARE 'WHAT' THE DESIRED RESULT IS
- IMMUTABLE
  - Object.freeze
  - Immutable.js
- FIRST CLASS FUNCTIONS
- CLOSURES (ENCAPSULATION)
```js
const createAdder = (x) => {
return (y) => x + y;
};

const add3 = createAdder(3);

add3(2) === 5;
add3(3) === 6;
```
- CURRYING
```js
  const add = x => y => x + y;
  
  function add(x) {
  	return function(y) {
  		return x + y;
  	};
  }
```

## 특징 (2)

- Declarative pattern
  - Imperative programs spend lines of code describing the specific steps used to achieve the desired results — the flow control: How to do things.
  - Declarative programs abstract the flow control process, and instead spend lines of code describing the data flow: What to do. The how gets abstracted away.
  - Array Functions : for devlarative pattern
    - filter
    - find
    - mao
    - reduce
    - every
    - some


## 핵심 개념

### Pure function
  - Given the same inputs, always returns the same output, and .. 참조 투명성 (Referential transparency)
  - Has no side-effects .. (Side-effect free)
### Function composition
  - the process of combining two or more functions in order to produce a new function or perform some computation
  - Function Chaining
### Avoid shared state
  - Shared state
    - any variable, object, or memory space that exists in a shared scope, or as the property of an object being passed between scopes
### Avoid mutating state
  - Immutability
    - An immutable object is an object that can’t be modified after it’s created. Conversely, a mutable object is any object which can be modified after it’s created.
    - Immutable Libraries
      - Seamless-immutable
      - Immutable JS
### Avoid side effects
  - A side effect is any application state change that is observable outside the called function other than its return value. 
  - Haskell and other functional languages frequently isolate and encapsulate side effects from pure functions using monads.

## How?

### 고계함수
- A higher order function is any function which takes a function as an argument, returns a function, or both.

## Libraries to support FP

- lodash
- RamdaJS
- RxJS


## 교재

- https://github.com/luijar/functional-programming-js

## Articles

- http://hughfdjackson.com/javascript/why-curry-helps/