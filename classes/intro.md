##Classes Intro

<div class="spec es6">ES6</div>


ES6 classes are syntactical sugar over the Objects and prototypes that we're used to working with. They simply offer a much nicer, cleaner and clearer syntax for creating these objects and dealing with inheritance.

**Old Class Contruction**

```javascript
function Person(name) {
    this.name = name
}

Person.prototype.getName = function() {
    return this.name;
}

Person.prototype.setName = function(name) {
    this.name = name
}

var person = new Person('Don');
person.getName(); //Don
person.setName('Paul');
person.getName(); //Paul
```

We are making a constructor function and then adding methods to its prototype. There are many different patterns that could be use to create a class (modular, factory, ...) and ES6 provides a canoncial way to define a Class.

**ES6 Class Contruction**

```javascript
class Person {

    constructor(name) {
        this.name = name;
    }

    getName() {
        return this.name;
    }

    setName(name) {
        this.name = name;
    }

}

var person = new Person('Don');
person.getName(); //Don
person.setName('Paul');
person.getName(); //Paul
```

The code is now semantically more readable and less code to write.
