##Function Parameters Spread

<div class="spec es6">ES6</div>

```javascript
function sentence(...words) {
    return words.join(' ');
}

function sum(...nums) {
    return nums.reduce((prev, curr) => prev + curr);
}

sentence('Who','is','this','Don','?')// Who is this Don?
sum(1,2,3)// 6
```

The function spread parameter(...args) is an array of the provide parameters to the function.
