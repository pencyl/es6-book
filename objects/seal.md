# Object.prototype.seal

<div class="spec es5">ES5</div>

Object.seal seals an object, stopping any further manipulation. It essentially makes the object *immutable*.

Object.seal will stop
- Properties being added
- Properties being removed
- Properties being changed *to or from accessors*


```javascript
var user = { name: 'Johnny Five', isAlive: true, arms: 2 };

Object.seal(user);

delete user.isAlive; // false
user.battery = 100; // 100
user.name = 'Johnny Six'; // 'Johnny Six'

user; // { name: 'Johnny Six', isAlive: true, arms: 2 }
```

Inside strict mode attempts to add or remove properties will result in TypeErrors
```javascript
var user = { name: 'Johnny Five' };

Object.seal(user);

user.legs = 2; // TypeError

user; // { name: 'Johnny Five' }
```

As we saw in the first example changing property values is allowed, but, they cannot be converted to getters or converted for getters to a value..
```javascript
var data = {};
Object.defineProperty(data, 'timestamp', { get: function() { return Date.now(); } });

data.timestamp; // 626649295

data.timestamp = Date.now(); // TypeError
```

The above is the ES5 way of defining a "getter", this is somewhat clearer with ES6...

```javascript
var data = {
    get timestamp() {
        return Date.now();
    }
};
data.timestamp; // 573955200
```

It's important to remember that values *that are other objects can still be changed*, unless they're sealed too.

```javascript
var error = { reason: 1 };
var data = { error: error, response: '' };

Object.seal(data);
data; // { error: { reason: 1 }, response: '' }

delete error.reason;

data; // { error: {}, response: '' }
```

You can check an object is "sealed" by using Object.prototype.isSealed.

```javascript
var user = {};

Object.isSealed(user); // false

Object.seal(user);

Object.isSealed(user); // true
```
