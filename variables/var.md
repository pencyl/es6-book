#var

<div class="spec es1">ES1</div>


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

The reason this doesn't break is, var's are function scoped. They are "hoisted", this is evaluated as is more like the following...

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

<br/>

### Hoisted loop variable

Here we have an empty array, we loop 3 times pushing a function to it. That function is intending to log out a string with the task number from `i`.

However, by the time we run each of these task functions. `i` turns out to always be 3.

`i` is essentially hoisted to be on par with the tasks array, and it's final value after `i++` is 3.

```javascript
var tasks = [];

for (var i = 0; i < 3; i++) {
    tasks[i] = function() { console.log('task number - ' + i); };
}


for (var y = 0; y < 3; y++) {
    tasks[y]();
}
// 'task number - 3'
// 'task number - 3'
// 'task number - 3'
```

<br/>
<br/>

One way to solve this is by wrapping function creation in another function, another scope...

```javascript
var tasks = [];

function createfunc(i) {
    return function() { console.log('task number - ' + i); };
}

for (var i = 0; i < 3; i++) {
    tasks[i] = createfunc(i);
}


for (var y = 0; y < 3; y++) {
    tasks[y]();
}
// 'task number - 0'
// 'task number - 1'
// 'task number - 2'
```
