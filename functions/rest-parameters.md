# Rest parameters

<div class="spec es6">ES6</div>


Think of it as "the rest"

```javascript
function foo(a, b, ...theArgs) {
    console.log(a, b, theArgs);
}
foo(1, 2, 3, 4, 5); // 1, 2, [3, 4, 5]
```

## Why not arguments?
- Arguments can't be named, it's always called `arguments`
- It's not a real array
- Can't be used with [arrow functions](/functions/arrow.md)
