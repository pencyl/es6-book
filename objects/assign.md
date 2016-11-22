# Object.prototype.assign

Part of ES5, now widely available.

Object.assign is used to copy all of the values and properties of an object to a new target object.

## Copying objects

It's good practice to use Object.assign rather than manipulating/copying references.

```javascript
var myObject = { foo: 'bar' };
var myNewObject = myObject;
myNewObject.foo = 'rad';

myNewObject // { foo: 'rad' }
myObject // { foo: 'rad' }, myObject was unintentionally manipulated
```

```javascript
var myObject = { foo: 'bar' };
var myNewObject = Object.assign({}, myObject);
myNewObject.foo = 'rad';

myNewObject // { foo: 'rad' }
myObject // { foo: 'bar' }
```

## Merging objects

```javascript
var defaults = { logging: true };
var myConfig = Object.assign({
    logLevel: 'verbose'
}, defaults);

myConfig // { logging: true, logLevel: 'verbose' }
```
