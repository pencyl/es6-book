# Object.prototype.freeze

<div class="spec es5">ES5</div>

Object.freeze does everything Object.seal does, but additionally stops values from being changed.

Object.freeze will stop
- Properties being added
- Properties being removed
- Properties being changed in any way

```javascript
var user = { name: 'Johnny Five', isAlive: true, arms: 2 };

Object.freeze(user);

delete user.isAlive; // false
user.battery = 100; // 100
user.name = 'Johnny Six'; // 'Johnny Six'

user; // { name: 'Johnny Five', isAlive: true, arms: 2 }
```

Inside strict mode attempts to change it will result in TypeErrors
```javascript
var user = { name: 'Johnny Five' };

Object.seal(user);

user.arms = 2; // TypeError

user; // { name: 'Johnny Five' }
```

Just like with isSealed, can check an object is "frozen" by using Object.prototype.isFrozen.

```javascript
var thing = {};

Object.isFrozen(thing); // false

Object.freeze(thing);

Object.isFrozen(thing); // true
```
