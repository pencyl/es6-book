# String.prototype.includes

<div class="spec es6">ES6</div>

Includes is self explanatory, you can check if a string contains another string.

Previously you could check that the indexOf the string is more than 0, but it's not that clear.

```javascript
'Hello Dave'.indexOf('Dave') > 0; // true
```

<br/>

Now the intent is much clearer...

```javascript
'Hello Dave'.includes('Dave'); // true
```
