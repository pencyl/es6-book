##Class getters and setters

<div class="spec es6">ES6</div>

```javascript
class Person {

	constructor(name) {
		this._name = name;
	}

	get name() {
		console.log(`getter fired for ${this.name}`);
		return this._name;
	}

	set name(name) {
		console.log(`setter fired for ${name}`);
		this._name = name;
	}

}

var person = new Person('Don');
person.name; //Don
person.name = 'Paul';
person.name; //Paul
```

Get and set allow us to use a bit of short hand to set variables and retrieve variables on the class.
