# Arrow functions

The "new function"

```javascript
var add = function (a, b) {
  return a + b;
}
```
Becomes
```javascript
var add = (a, b) => a + b;
```

### What's different

- It's faster to type, maybe
- Don't need ```function``` keyword
- Don't always need parentheses `()`
- Don't always need curly brackets `{}`
- They're always function expressions, cannot be bound, cannot be named

#### Parameters
The arrow function is composed with a parameter list, in a surrounding ```()``` if there are more than one.

Two params, need parentheses
```javascript
var add = (a, b) => { a + b };
add(1, 2); // 3
```
One param, omit parentheses
```javascript
var double = a => { a * 2 };
double(1); // 2
```
Zero params, just parentheses
```javascript
var foo = () => 1000;
foo(); // 1000
```

> Note: All existing functionality of parameters are still available (rest parameters, default values, destructuring)

#### Body

The function body only needs to be enclosed by curly brackets ```{}``` if there's only a single expression.

Single expression
```javascript
(one, two) => one + two;
```

Multiple expressions
```javascript
(one, two) => { var sum = one + two; return sum * two; }
```

#### Return

Similarly the return keyword can also be omitted, it's implied before the expression
```javascript
(one, two) => one + two;
```
Is the same as...
```javascript
(one, two) => { return one + two };
```


#### Context

Usually each ```function``` binds it's own ```this```, often this is worked around by defining a "self" or a "that" in the upper scope.

#### Timer example

Here we've got a really simple timer, the count method increments 'number' on the instance of the counter.
```javascript
function MyCounter () {
    this.number = 0;
}

MyCounter.prototype.count = function () {
    var self = this;
    setInterval(function () {
        self.number++;
    }, 1000);
}

var count = new MyCounter();
count.count();
```

The setInterval uses an anonymous function as a callback, this introduces a new context for `this`. So we have to create a link to it with `self` outside it's scope.

As arrow functions don't introduce scope, changing the anonymous function to an arrow function solves the need for `self`.

```javascript

MyCounter.prototype.count = function () {
    setInterval(() => {
        this.number++;
    }, 1000);
}
```

##### DOM example

```javascript
$('.timer').each(function () {
  var that = this;

  setInterval(function () {
    $(that).text(Date.now());
  }, 1000);
});

```

Fat arrow doesn't have scope issue because the ```this``` binding is not dynamic, it is lexical, like ```let```

```javascript
$('.timer').each(function () {
  setInterval(() => $(this).text(Date.now()), 1000);
});
```

### Caveats

As we've seen, the lexical scope of ```this``` within an arrow function body is different to a normal anonymous function.

Whilst it's tempting to use the terse new syntax and refactor old code, you need to bear it in mind as it can have unintended consequences.

For example, this mocha test
```javascript
describe('our test', () => {
  this.timeout(100);
});

// TypeError: this.timeout is not a function
```

Now the describe block uses an arrow function it can't access the mocha context.

We also lose the ability to use access the arguments variable, as it doesn't have it's own scope we get the global arguments

```javascript
() => {
  var level = arguments[0]; // global
  var message = arguments[1]; // global
}
```

> It's also not possible to use an arrow function as a "generator"

#### Another example
```javascript
var viewController = {

  render: function(data) {
    document.write(data);
  },

  getData: function() {
    // ajax
    this.render('<p>old school</p>');
  }
}

viewController.getData(); // 'meh'
```

Changing getData to use an arrow function looks neater, but changes ```this```
```javascript
getData: () => {
  // ajax
  this.render('<p>old school</p>');
}
viewController.getData(); // nothing
```

#### Naming

Like anonymous functions they don't strictly have a name, but can still be assigned to a variable
```javascript
var myArrowFunc = () => { return 'hey' };
myArrowFunc(); // hey
```

#### Real life usage

In the real world, the arrow function is best used to replace simple inline anonymous functions...

```javascript
var simpleArray = [1,2,3];
var doubled = simpleArray.map(function(num) {
  return num * 2
});
console.log(doubled); // [2,4,6]
```

Becomes

```javascript
var simpleArray = [1,2,3];
var doubled = simpleArray.map(n => n * 2);
console.log(doubled); // [2,4,6]
```
