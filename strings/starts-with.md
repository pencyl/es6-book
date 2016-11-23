# String.prototype.startsWith

<div class="spec es6">ES6</div>


Checking a string starts with something is a fairly common task.

Currently you can check a string starts with something using `.indexOf()`

Checking the indexOf a particular string is 0, we know the string *beings* with that.

```javascript
'https://blah.com'.indexOf('https') === 0; // true

'http://blah.com'.indexOf('https') === 0; // false
```

<br/>

Now we can use the built in startsWith method making this a bit more reliable and more readable, our intent is much clearer.

```javascript
'https://blah.com'.startsWith('https'); // true
```

Like indexOf, startsWith accepts an index. We could easily ignore the first 1/2 characters by passing in an index

```javascript
'https://blah.com'.startsWith('blah', 8); // true
```
