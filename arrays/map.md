# Array.prototype.map

<div class="spec es5">ES5</div>

Part of ES5, now widely available.

Returns a new array with the result of calling a function on each item in the array.

The function passed in receives the current item, it's index and the full array as parameters.

Allows you to easily manipulate or add to each item in an array, without looping or editing the original.

```javascript

const cars = [
    { color:'red', engineSize: 1.0 },
    { color:'red', engineSize: 1.6 },
    { color:'blue', engineSize: 2.0 },
    { color:'green', engineSize: 3.0 }
];

const engineSizes = cars.map(function(car) {
    return {
        engineSize: car.engineSize
    }
});

console.log(engineSizes); // new array
cars[0].engineSize = 5;
// engineSizes not affected
```

Useful for omitting unneeded keys, for example...

```javascript
const results = [
    { id: 1, name: 'Matt' },
    { id: 2, name: 'Cal' },
];

res.send(results.map(function (result) {
    return {
      name: result.name
    }
});
// res.send called [{ name: 'Matt' }, { name: 'Cal' }]
```

> There's also an optional second parameter 'thisArg', it is the value to use as this (the context) for the function passed in to map.
