# String.prototype.repeat

<div class="spec es6">ES6</div>

Repeat can be quite handy, it allows you to repeat a string n times.

<br/>
<br/>

Previously you'd probably use a loop to do this.

```javascript
var repeatedString = 'test';
for (var i = 0; i <= 10; i++) {
    repeatedString = repeatedString + repeatedString;
}
repeatedString; // 'testtesttesttesttesttesttesttesttesttest'
```

<br/>

Now with ES6 we can use String.repeat...

```javascript
'test'.repeat(10); // 'testtesttesttesttesttesttesttesttesttest'
```
