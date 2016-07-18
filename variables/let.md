# let

let's are the new var, they work very much like var. The main difference is that the scope of a var variable is the entire enclosing function. let's are block scope variables. Unlike a var their scope is limited to the block **{}** they are declared in.

```javascript
function foo () {
	var a = 1;

	{
		let b = a * 10;
		console.log(b); // 10
		var a = 'whatever';
	}

	console.log(a); // whatever
	console.log(b); // "ReferenceError: b is not defined
}

foo();
```

### The TDZ (Temporal Dead Zone)
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
To avoid TDZ errors, always declare let's at the top of their block

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
