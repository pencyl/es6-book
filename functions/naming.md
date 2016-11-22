# Function names

<div class="spec es6">ES6</div>


This has been supported in most engines prior to ES6, but with ES6, it becomes part of the spec.

```javascript
var foo = function () { throw('this is from an anonymous function'); }
console.log(foo.name); // 'foo'
```

This is useful when an anonymous function throws an error, the name is inferred from the variable it's assigned to and we see it in the stacktrace...

<img src="/img/func-name.png" alt="Stacktrace when calling the 'foo' function" />
