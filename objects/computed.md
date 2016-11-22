# Computed properties

<div class="spec es6">ES6</div>


```javascript
function getCar(make) {
    var carObj = {
        make: make,
    }
    carObj['is' + make] = true;

    return carObj;
}

getCar('BMW'); // {"make":"BMW","isBMW":true}
```

This can be simplified with ES6 computed properties.

```javascript
function getCar(make) {
    return {
        make, // same as make: make
        ['is' + make]: true // we just computed the key name
        [ 'was' + (() => make)() ]: true //we can run an expression to create key too
    }
}

getCar('BMW'); // {"make":"BMW","isBMW":true, "wasBMW":true}
```
