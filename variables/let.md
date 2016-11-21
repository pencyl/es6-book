# let

let's are the new var, they work very much like var. The main difference is that the scope of a var variable is the entire enclosing function. let's are block scope variables.

[Unlike var](/variables/var), let's scope is limited to the block `{}` they are declared in.

## Blocks
What's a block again?

Blocks are completely valid and have been implemented since JavaScript 1.0

This is valid...
```javascript
function blocks() {
  var message = 'hi';

  {
    return message;
  }
}

blocks(); // 'hi'
```

Up until now you've probably only used blocks to control flow statements, e.g. `if, else, for & while`

## Block scoped variables using let

```javascript
function varScope () {

    if (true) {
        var price = 10;
        console.log(price); // 1
    }

    console.log(price); // 10!
}

varScope();
```

The same function rewritten to use let

```javascript
function letScope () {

    if (true) {
        let price = 10;
        console.log(price); // 1
    }

    console.log(price); // "ReferenceError: price is not defined
}

letScope();
```
The price variable defined in our `if (true)` block is only scoped to that block.

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

Multiple blocks could reuse the same variable name when using let, as  their scope is limited to the block they're declared in

```javascript
function letScope () {

    if (true) {
        let price = 10;
        console.log(price); // 1
    }

    {
      let price = 100000;
      console.log(price); // 100000
    }

    console.log(price); // "ReferenceError: price is not defined
}

letScope();
```

### The TDZ (Temporal Dead Zone)
What was that ReferenceError all about?

var's are "hoisted", which allows us to use them before they're defined.
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
To avoid TDZ errors, consider declaring let's at the top of their block

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

### More Examples

Here `i` is used multiple times, but it works because `i` is a new instance on each iteration of the loop.

This wouldn't work with `var` as it would refer to the same variable in each iteration of the loop.

```javascript
var $list = $('#list')

for (let i = 1; i <= 5; i++) {
  let item = $('<li>' + 'Item ' + i + '</li>');

  item.bind( 'click', function() {
    console.log('You clicked item ' + i);
  });
  $list.append(item);
}
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
