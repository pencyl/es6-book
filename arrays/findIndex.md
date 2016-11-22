# Array.prototype.findIndex

<div class="spec es6">ES6</div>

Returns the index of the item found by the testing function.

```javascript
const cars = [
    { color:'red', engineSize: 1.0},
    { color:'blue', engineSize: 2.0},
    { color:'green', engineSize: 3.0}
];

cars.findIndex(function(car) {
    return car.color === 'blue'
});

// or with an arrow function

cars.findIndex(c => c.color === 'blue'); // 1
```

### Putting it all together

Lets say we want to replace a car that matches certain criteria with a new car, in the same position in the array.

```javascript

const cars = [
    { color:'red', engineSize: 1.0},
    { color:'blue', engineSize: 2.0},
    { color:'green', engineSize: 3.0}
];

const newCar = {
    color: 'purple',
    engineSize: 3.4
}

function replaceCar(replacement, car) {
    // find the index of the car we want to replace,
    // with the replacement testing function
    const index = cars.findIndex(replacement);
    // return a new array using the existing cars array,
    // up until the index of the car we're replacing
    // then the newCar
    // then the rest of the cars array
    return [
        ...cars.slice(0, index),
        newCar,
        ...cars.slice(index + 1)
    ];
}

replaceCar(c => c.color === 'blue', newCar);
// [{'color':'red','engineSize':1},{'color':'purple','engineSize':3.4},{'color':'green','engineSize':3}]
```
