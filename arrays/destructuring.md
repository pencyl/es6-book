# Destructuring

<div class="spec es6">ES6</div>


Destructuring assignments give us a much cleaner way of extracting values from arrays.

Consider this array
```javascript
var weekDays = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri'];
```

If we wanted to get each day as a separate variable, we could do something like this...
```javascript
var monday = weekDays[0];
var tuesday = weekDays[1];
var wednesday = weekDays[2];
var thursday = weekDays[3];
var friday = weekDays[4];
```

With destructuring we can extract all the days, as individual variables with a single line of code..
```javascript
var [monday, tuesday, wednesday, thursday, friday] = weekDays;
console.log(monday); // 'Mon'
```

### Omitting values

If we wanted to omit values, just don't pass in a name...
```javascript
var [a, ,b] = [1, 2, 3];
console.log(a, b); // 1, 3
```

### Restricting data returned

Consider a function that returns 3 things and you want only 2.

```javascript
var foo = () => {
    return [1, 2, 3];
};

var [a, b] = foo();
console.log(a, b); // 1 2
```

### Swapping variables without temporary variables

```javascript
var a = 1, b = 2;
[b, a] = [a, b];
console.log(a, b); // 2, 1
```

### Default values

Variables can even be assigned defaults incase the value pulled from the array isn't defined.
```javascript
var [a = 1, b = 2, c = 3] = [5, 10];
console.log(a, b, c); // 5, 10, 3
```
