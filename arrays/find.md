# Array.prototype.find

Returns the first match found by the testing function.

The testing function receives the current element, index and full array as parameters.

> Having the full array as the 3rd parameter is useful if needed in the testing function body and not in scope.

```javascript
const cars = [
  { color:'red', engineSize: 1.0},
  { color:'red', engineSize: 1.6},
  { color:'blue', engineSize: 2.0},
  { color:'green', engineSize: 3.0}
];

cars.find(function(car) {
  return car.color === 'red'
});

// or with an arrow function

cars.find(c => c.color === 'red' );

// { color:'red', engineSize: 1.0}
// returns first match
```

> There's also an optional second parameter 'thisArg', it is the value to use as this (the context) for the testing function.
