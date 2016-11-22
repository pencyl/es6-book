# Default parameters

Previously in JavaScript if you wanted to use default parameters you'd have to use a hack like this:

```javascript
function oldWay(a, b) {
    a = a || 1;
    b = b || 10;
    return a * b;
}
oldWay(); // 10
```

It works, but it's not perfect. What if ```a``` is ```0```?

```javascript
oldWay(12, 0); // 120 (0 is falsy)
```

Then there's the slippery slope of...

```javascript
function oldWay(a, b) {
    if (a === undefined) {
        a = 10;
    }
}
```

## ES6 to the rescue

With ES6 we can now handle default parameters properly...

```javascript
function newWay(a = 1, b = 10) {
    return a * b;
}
newWay(); // 10
newWay(0); // 0
newWay(1, 2); // 2
newWay(undefined, 11); // 11 (undefined is "missing")
newWay(null, 11); // 0 (null is explicitly null)
```

Default parameters can also be expressions...

```javascript
function foo(a = 1 + 1, b = 10) {
    return a * b;
}
foo(); // 20
```

You can call other functions available within the current scope, like this node module....

```javascript
var config = require('config');

export function urlBuilder(host = config.get('host'), port = 27017) {
    return 'mongod://' host + ':' + port;
}

// assuming config.get('host') returns 'hostname'
urlBuilder(); // mongod://hostname:27017
```

They can even be self invoking functions

```javascript
function madness(a = (function(){ return 10 }()), b = 5) {
    return a * b;
}

madness(); // 50
```

> If you ever find yourself doing this, take a step back

## Use cases

### Ensuring type

The function below, handleResults uses the array method 'map'. If something that wasn't an array was passed in a TypeError would be thrown.


```javascript
function handleResults(results = []) {
    // if results wasn't an array we'd get an error here
    // "TypeError: Cannot read property 'map' of undefined
    // previously we'd have to check results exists & it's an array
    return results.map(function (result) {
        return {
            id: result.id
        }
    });
}
```

This is a really useful refactor, it stops you having to add an extra line of code to check.
```javascript
if (!results || !results.length) { return false; }
```

### What about a required parameter?

Default params still won't help you enforce a required parameter, but, we can use a default param expression to our advantage to achieve it.

```javascript
function required () {
    throw new Error('Required param missing');
}

function foo (baz = 2, iReallyNeedThis = required()) {
    return baz + iReallyNeedThis;
}

foo(1, 2); // 3
foo(1, undefined); // "Error: Required param missing
```
