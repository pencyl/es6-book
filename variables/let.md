# let

<div class="spec es6">ES6</div>

let's are "the new var", they work very much like var. They define a variable and that variable can be changed, incremented, decremented, deleted etc

<br/>

However, the difference is a *[vars](/variables/var)* scope is limited to the enclosing function, a *let*'s scope is limited to the block `{}` they are declared in.

## Blocks
What's a block?

Blocks are completely valid and have been implemented since JavaScript 1.0.

Up until now you've probably only used blocks to control flow statements, e.g. `if, else, for & while`.

```javascript
function blocks() {
    var message = 'hi';

    {
        return message;
    }
}

blocks(); // 'hi'
```

## Block scoped variables using let

Here's a basic function using a var to define "price".

```javascript
function varScope () {

    if (true) {
        var price = 10;
        console.log(price); // 10
    }

    console.log(price); // 10!
}

varScope();
```

The var has been [hoisted](/variables/var) and is available even before it is defined.

<br/>

The same function rewritten to use let...

```javascript
function letScope () {

    if (true) {
        let price = 10;
        console.log(price); // 10
    }

    console.log(price); // "ReferenceError: price is not defined
}

letScope();
```
The price variable defined in our `if (true)` block is only scoped to that block.

A reference error is now thrown if you try to access the price variable outside it's block.

Let's swap the values of an array, using a temporary variable, but keeping that temporary variable hidden away in it's own block.

```javascript
function swap(values) {
    {
        let temp = values[0];
        values[0] = values[1];
        values[1] = temp;
    }

    console.log(values); // [2, 1]
    console.log(temp); // "ReferenceError: temp is not defined
}

swap([1, 2]);
```

Nice, "temp" only exists in those 3 lines in it's enclosing block.

<br/>

As their scope is limited to the block they're declared in, multiple blocks can be used to allow us to reuse the same variable name multiple times...

```javascript
function letScope () {

    if (true) {
        let price = 10;
        console.log(price); // 10
    }

    {
        let price = 100000;
        console.log(price); // 100000
    }

    console.log(price); // "ReferenceError: price is not defined
}

letScope();
```

<br />

Back to our loop example where `i` is hoisted. Changing this to a let makes it work with no function creator!

```javascript
var tasks = [];

for (let i = 0; i < 3; i++) {
    tasks[i] = function() { console.log('task number - ' + i); };
}

for (var y = 0; y < tasks.length; y++) {
    tasks[y]();
}
// 'task number - 0'
// 'task number - 1'
// 'task number - 2'
```

### The TDZ (Temporal Dead Zone)
What was that ReferenceError all about?

As we've covered, var's are "hoisted", which allows us to use them before they're defined.
```javascript
function baz() {
    bar();
    var a = 1;
}

// is interpreted as
function baz() {
    var a;
    bar();
    a = 1;
}
```

With let

```javascript
console.log(a); // throws a ReferenceError
let a = 'hey';
```

let & const declarations **do not hoist**. Unlike var's they will not return undefined if accessed before initialization, they will throw an error!

### Best practices
To avoid TDZ errors, consider declaring let's at the top of their block.

```javascript
function name (obj) {
    var name = '';

    { let tmp;

        tmp = obj.name;
        name = tmp;
    }

    return name;
}

name({name: 'matt'});
```

### Should let replace var?
It's quite possible your codebase relys on non blocked scoped closure in loops like above, or, you're accidentally accessing hoisted vars like so...

```javascript
myObj = {};

// loads of code...
var myObj;
```
Find & replacing all of you're existing vars to lets could lead to issues. If you do want to use it heavily you should refactor on a case by case.

Sometimes, it might even make more sense to use a mix of var and let

```javascript
function maxWidth() {
    var width = 10;

    if (width > 100) {
        let a = width * 2;
        console.log(a);
    }

    if (width > 500) {
        let b = width / 2;
        console.log(b);
    }

    console.log(width);
}
```
