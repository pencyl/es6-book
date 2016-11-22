##Static variables and methods

<div class="spec es6">ES6</div>

We can both set and inherit static methods and variables in ES6 class construction.

```javascript

class Person {

    constructor(name) {
        this.name = name;
    }

    static version = 0.0.1

    static desc() {
        return `This is a description of this Person Class`
    }

}

Person.version; 0.0.1
Person.desc(); //This is a description of this Person Class

```

We can also set the static variables and methods by:

```javascript

class Person {
    constructor(name) {
        this.name = name;
    }
}

Person.version = 0.0.1
Person.desc = () => This is a description of this Person Class;

```

>Note that in ES6 we also can inherit static methods and variables. This wasn't possible in ES5.
