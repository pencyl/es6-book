##Class getters and setters

<div class="spec es6">ES6</div>

Previously getters and setters existed in ES5, you would've used `Object.defineProperty` to set them...

```javascript
var player = {
    level: 5
};

Object.defineProperty(player, 'health', {
    get: function() {
        return player.level * 10.5;
    }
});

console.log(player.health); // 52.5
```


```javascript
class Person {

	constructor(name) {
		this._name = name;
	}

	get name() {
		return this._name;
	}

	set name(name) {
		this._name = name;
	}

}

var person = new Person('Don');
person.name; //Don
person.name = 'Paul';
person.name; //Paul
```

Get and set allow us to use a bit of short hand to set variables and retrieve variables on the class.
