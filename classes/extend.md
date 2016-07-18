##Inheritance and Extending

We can extend out classes to inherit from a parent/base class. We then have access to all the methods and variables from the parent that we can add too in our new subclass.

```javascript
class Person {

    constructor(name) {
        this.name = name;
    }

    getName() {
        return this.name
    }

}

class Introvert extends Person {

    constructor(options) {
        super(options);
        this.quiet = true;
    }

    getName() {
        const name = super.getName();
        return `${name} is quiet`;
    }

}

const person = new Introvert('Don');
person.name; //Don
person.quiet; //true
console.log(person.getName()); //Don is quiet
```

Super() takes all the variables and methods set in the parent class and allows them to be reused in the subclass. We use super() in the constructor to inherit the name variable and super() in the getName() method.

Extends is the keyword we use to make the Introvert class inherit from the Person class.

>Note that in ES6 we also can inherit static methods and variables. This wasn't possible in ES5.
