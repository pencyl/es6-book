# Array.prototype.includes

<div class="spec es6">ES6</div>

This replaces a common pattern when checking an array includes a value.

<br/>
<br/>

```javascript
var arr = [1, 2, 3];
if (arr.indexOf(1) !== -1) {
    console.log('array has 1');
}
```

This can now be refactored to...

```javascript
var arr = [1, 2, 3];
if (arr.includes(1)) {
    console.log('array has 1');
}
```
#### Why not 'includes' like string?
The proposal was originally for `Array.prototype.contains`. MooTools extended the native array prototype, causing a conflict. Due to the huge number of sites still using it, it was decided to use `includes` and rename `String.prototype.contains` to `String.prototype.includes`.
