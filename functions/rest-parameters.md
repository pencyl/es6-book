# Rest parameters

<div class="spec es6">ES6</div>


Here, we've got a basic calculator function. The first argument is expected to be the type of operation, and all subsequent arguments should be the numbers for the calculation.

Previously, we'd have to loop over the arguments array to work all of this out...

```javascript
function calculator() {
    var sum = 0;
    var nums = [];
    var type = arguments[0];

    for (var i = 1; i < arguments.length; i++) {
        nums.push(arguments[i]);
    }



    for (var y = 0; y < nums.length; y++) {
        if (type === 'add') {
            sum = sum + nums[y];
        }
    }

    return sum;
}

calculator('add', 1, 2, 3, 4); // 10
```
<br/>

This basic calculator can be rewriten using a rest parameter. We can now define type as a genuine function argument, and have "the rest" of the arguments as an array called `nums`.

<br/>

```javascript
function calculator(type, ...nums) {
    var sum = 0;

    for (var y = 0; y < nums.length; y++) {
        if (type === 'add') {
            sum = sum + nums[y];
        }
    }

    return sum;
}

calculator('add', 1, 2, 3, 4); // 10
```

## Why not arguments?
- It's not clear
- It's not a real array
- Arguments can't be named, it's always called `arguments`
- Can't be used with [arrow functions](/functions/arrow.md) due to the scope
