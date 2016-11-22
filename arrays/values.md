# Array.prototype.values  

Part of ES5, now widely available.

Returns a new **Array Iterator** that contains the values for each index in an array.

```javascript
const cars = [
    { color:'red', engineSize: 1.0},
    { color:'red', engineSize: 1.6},
    { color:'blue', engineSize: 2.0},
    { color:'green', engineSize: 3.0}
];
cars.values(); ArrayIterator
const carValuesIterator = cars.values();
carValuesIterator.next(); // { 'value': { 'color':'red', 'engineSize': 1.0 }, 'done':false }
carValuesIterator.next(); // { 'value': { 'color':'red', 'engineSize': 1.6 }, 'done':false }
carValuesIterator.next(); // { 'value': { 'color':'blue', 'engineSize': 2.6 }, 'done':false }
```
