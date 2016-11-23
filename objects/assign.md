# Object.prototype.assign

<div class="spec es5">ES5</div>


Part of ES5, now widely available.

Object.assign is used to copy all of the values and properties of an object to a new target object.

## Copying objects

It's good practice to use Object.assign rather than manipulating/copying references.

```javascript
var myObject = { foo: 'bar' };
var myNewObject = myObject;
myNewObject.foo = 'rad';

myNewObject; // { foo: 'rad' }
myObject; // { foo: 'rad' }, myObject was unintentionally manipulated
```

## The target parameter
The first parameter of Object.assign is the target. Without setting it, objects are just merged into each other.

Most times you'll want a fresh object returned rather than manipulating existing ones.

```javascript
var thing = { a: 1 };
var otherThing = { b: 1 };
var newThing = Object.assign(thing, otherThing);

newThing; // { a: 1, b: 1 }
thing; // { a: 1, b: 1 }
newThing === thing; // true
```

Now we'll assign to an empty source object. `newThing` is now a genuinely new object, it's not a reference to `thing` and any subsequent changes to it will not affect `thing`.
```javascript
var thing = { a: 1 };
var newThing = Object.assign({}, thing);

newThing; // { a: 1 }
thing; // { a: 1}
newThing === thing; // false

newThing.foo = 'hi';

newThing; // { a: 1, foo: 'hi' }
thing; // { a: 1}
```

## Merging objects
```javascript
var defaults = { logging: true };
var myConfig = Object.assign({}, defaults, { logLevel: 'verbose' });

myConfig; // { logging: true, logLevel: 'verbose' }
```

## Multiple sources

You can pass multiple source objects to Object.assign, properties are overwritten by other source objects in the parameters order.

```javascript
var o1 = { foo: 1 };
var o2 = { foo: 2 };
var o3 = { foo: 3 };
var result = Object.assign({}, o1, o2, o3);

console.log(result); // { foo: 3 }
```
