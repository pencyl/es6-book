# Property value shorthand

<div class="spec es6">ES6</div>


You've probably written code that assigns properties using variables of the same name before.

<br/>

```javascript
var url = 'http://google.com';
request({
    url: url
}).then(...)
```

In ES6 you can shorten this syntax...

```javascript
var url = 'http://google.com';
request({
    url // same as url: url
}).then(...)
```

#### console.log trick

It's fairly common to log the state of a variable like the following

```javascript
const myVar = 124;
console.log('myVar', myVar); // myVar 124
```

With object destructing we can simplify this by logging an object, but not specifying the key name, the variable name will be used.

```javascript
const myVar = 124;
console.log({ myVar }); // {myVar: 124}
```

Arguably what is logged to the console isn't as clear, as the object is only there for sake of simplifying the code.

But, this method is less prone to typing errors and shorter to type.
