# Object.prototype.freeze

<div class="spec es5">ES5</div>

Object.freeze freezes an object, stopping any further manipulation. It essentially makes the object *immutable*.

Outside strict mode attempts to change it will silently fail

```javascript
var obj = { foo: 'bar', deleteMe: true };
delete obj.deleteMe;
obj // { foo: 'bar' }

Object.freeze(obj);

obj.newKey = 'hi'; // silent failure
obj // { foo: 'bar' }
```

Inside strict mode attempts to change it will result in TypeErrors
```javascript
var obj = { foo: 'bar', deleteMe: true };
delete obj.deleteMe;
obj // { foo: 'bar' }

Object.freeze(obj);

obj.newKey = 'hi'; // TypeError
obj // { foo: 'bar' }
```
