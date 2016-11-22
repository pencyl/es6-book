# Class Decorators

<div class="spec es6">ES6</div>

Decorators are a way of enriching your Classes. They provide similar functionality to Inheritence or Mixins.

A Class Decorator is used to add extra methods or variables to a class. It works just like extend in class construction but has the advantage that is doesn't rely on chained inheritance and decorators can be mixed and matched.

```javascript
function addCost(sum) {
    return function decorator(classDecorator) {
        classDecorator.prototype.cost = sum;
        classDecorator.prototype.ring = () => {
            alert('beep-beep-beep');
        };
    }
}

```

We define our class decorator. We have access to the prototype of the instansiated class.

```javascript
@addCost(50)
class PhoneBox {
    constructor() {
        this.model = "Big Red";
        this.size = 100;
    }
}

const phoneBox = new PhoneBox();
console.log(phoneBox.cost) // 50
console.log(phoneBox.ring()) // alerts beep-beep-beep
```

We add the decorator before the class with an **@** prefix. We can pass params in the decorator too.
