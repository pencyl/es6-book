# Array.prototype.keys

Part of ES5, now widely available.

Returns a new **Array Iterator** that contains the keys for each index in an array.

```javascript
const cars = [
  { color:'red', engineSize: 1.0},
  { color:'red', engineSize: 1.6},
  { color:'blue', engineSize: 2.0},
  { color:'green', engineSize: 3.0}
];
cars.keys(); ArrayIterator
const carKeyIterator = cars.keys();
carKeyIterator.next(); // { value: 0, done: false }
carKeyIterator.next(); // { value: 1, done: false }
```
