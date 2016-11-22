# Array.prototype.filter

Part of ES5, now widely available.

Returns an array of matching items which the provided filtering function returns true.

The filtering function receives the value of the current element, it's index and the full array as parameters.

```javascript
const cars = [
    { color:'red', engineSize: 1.0},
    { color:'red', engineSize: 1.6},
    { color:'blue', engineSize: 2.0},
    { color:'green', engineSize: 3.0}
];

cars.filter(function(car) {
  return car.color === 'red'
});

// or with an arrow function

cars.filter(c => c.color === 'red');

// [{ color:'red', engineSize: 1.0}, { color:'red', engineSize: 1.6}]
// returns array of matches
```

> There's also an optional second parameter 'thisArg', it is the value to use as this (the context) for the filtering function.
