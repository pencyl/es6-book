# const

<div class="spec es6">ES6</div>


const isn't about protected, frozen, constant or immutable variables. The only constant is the *binding*, it's a immutable reference to a binding. Like let, const's are block scope.

```javascript
const foo = [];
foo.push({something: 'new'});
console.log(foo);
// [{someting: 'new'}]
```

If a const is a complex variable like an array or object, it can still have it's contents modified.

It just can't be reassigned...

```javascript
const foo = [];
foo = 1;
// Uncaught TypeError: Assignment to constant variable.
```

> Like let's const's are also *block scoped*

## What's the point?
Whilst it doesn't make a variable immutable, it's still very useful for showing purpose and can easily be linted.

<img src="/img/const-error.png" height="150" />

> Don't rely on it for behaviour

> Think about it more as signalling intent

> See [Object.freeze](/objects/freeze.html) for objects, or [Symbols](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol) for strings
