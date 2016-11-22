# Simple Generator Function

<div class="spec es6">ES6</div>

A generator function is used for defining an iterator that can maintain its own state. The generated iterator can also be paused and resumed.

```javascript
function *Count() {
  yield 1;
  yield 2;
  yield 3;
  return 4;
}
```

The generator function is defined with an asterisk (*) and has one or more yield expressions.

```javascript
const count = new Count();
```

We invoke the Count() generator function to the newcount constant.

```javascript
count.next(); // { value: 1, done: false}
count.next(); // { value: 2, done: false}
count.next(); // { value: 3, done: false}
count.next(); // { value: 4, done: true}
```

count is now iterable. We can step through each iteration when we call next().

The returned object has a value, which is yielded by the generator function, and a done boolean, which indicates if we have complete all yields.

```javascript
for (let v of Count()) {
    console.log(v); //1,2,3,4
}
```

We can iterate through the count with the for-of loop.

```javascript
[...count] //[1,2,3]
```

We can convert the iterator in to a simple array using the spread operator.
