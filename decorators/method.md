# Method Decorators

Decorators are a way of enriching your methods.

A Method Decorators take the original method and then augment it, and finally return it. This means we can add extra functionality to a method and share this functionality between many different classes.

```javascript
function isProtected(target, name, methodDecorator) {
    methodDecorator.writable = false;
    return methodDecorator;
}

function isDepreciated(target, name, methodDecorator) {
    console.warn(`${name} is deprecated`);
    return methodDecorator;
}
```

We define our method decorators. We have access to the method and it object definition.

```javascript
class CellPhone {
    constructor() {
        this.model = "iPhone";
        this.size = 1;
    }

    @isProtected
    _internal() {
        const pin = 1234
        return pin;
    }

    @isDepreciated
    oldMethod() {
        return 'steam power';
    }
}
```

We add the decorator before the our chosen methods with an **@** prefix.

```javascript
const cellPhone = new CellPhone(); //Reports Warning of OldMethod being deprecated

console.log(cellPhone._internal) // shows _internal()
cellPhone._internal = () => 'changed';
console.log(cellPhone._internal) // still shows _internal() and ignores method re-write
```

> **Core Decorators**

> There are libraries being made at the moment that provide method decorators to help build your ES6 applications. A good library is [Core Decorators](https://github.com/jayphelps/core-decorators.js) by Jay Phelps.