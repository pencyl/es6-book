# Array.prototype.find

Returns the first match found by the testing function.

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
