##Class Constructor

<div class="spec es6">ES6</div>

The class constructor is auto-invoked on Class instansiation. It replaces any init() function or IIFE.

```javascript
class Person {
    constructor(name) {
        this.name = name;
        this.gender = (this.name === 'bob') ? 'male' : 'female'
    }
}

const person = new Person('Bob');
person.name; //Bob
person.gender; //male
```

The constructor also can take params when invoked to add to the instansiated object.
