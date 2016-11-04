#var

## Scope

var's scope are limited to functions

```javascript
var name = 'Rick';
​
​function getName () {
	var name = 'Morty'; // local variable, only available inside getName();
	console.log(name); // 'Morty'
}
console.log(name); // 'Rick'

getName();
```

## Hoisting

```javascript
function getPrice (productName) {
  if (productName === 'whisky') {
    var price = 25.99;
  }
  return price;
}
getPrice('whisky') // 25.99

getPrice('something else') // undefined
```

The reason this doesn't break is, var's are function scoped. They're "hoisted" and what this is evaluated as is more like the following...

```javascript
function getPrice (productName) {
  var price;
  if (productName === 'whisky') {
    var price = 25.99;
  }
  return price;
}
getPrice('whisky') // 25.99

getPrice('something else') // undefined
```
