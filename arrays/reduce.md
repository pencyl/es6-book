# Array.prototype.reduce

<div class="spec es5">ES5</div>

Reduce applies a function against an array, reducing the array to a single value.

Reducing is fairly simple, you might have previously done something like this...

```javascript
var bits = ['a', 'b', 'c'];
var message = '';

for (var i = 0; i < bits.length; i++){
    message += bits[i];
}

message; // abc
```

<br/>

This can be refactored to use reduce.

<br/>

It's an array method and it takes 2 arguments, an accumulator function and an optional initialValue.

The accumulator function has 4 arguments, accumulator, currentValue, currentIndex & array.

<br/>

##### accumulator
At first this is the initial value, then it becomes the previously returned value.
In the below example it would be "a", then "ab", then "abc".

##### currentValue
This is simply the current value in the array, "a", "b" then "c".

##### currentIndex
This is just the index of the value in the array the accumulator is currently on. 0, 1 then 2.

##### array
This is the whole array reduce has been called on.

<br/>
```javascript
var bits = ['a', 'b', 'c'];

var message = bits.reduce(function(accumulator, currentValue, currentIndex, array) {
    return accumulator + currentValue;
}, []);

message; // abc

// or with an arrow function
var message = bits.reduce((a, b) => a + b);
```
