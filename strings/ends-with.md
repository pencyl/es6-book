# String.prototype.endsWith

<div class="spec es6">ES6</div>

Like startsWith, checking a string ends with something is common and indexOf is regularly used.

```javascript
function isJpg (name) {
    return name.indexOf('jpg') > 0;
}
isJpg('photo.jpg'); // true
```

But this isn't very robust.

```javascript
isJpg('photojpg.gif'); // true
```

So, again, we could write more code.

```javascript
function isJpg (name) {
    var lastThreeCharacters = name.length - 3;
    return name.indexOf('jpg', lastThreeCharacters) > 0;
}
isJpg('photo.jpg'); // true
isJpg('photojpg.gif'); // false
```

Now, we can simplify this in ES6.

```javascript
function isJpg (name) {
    return name.endsWith('jpg');
}
isJpg('photo.jpg'); // true
isJpg('photojpg.gif'); // false
```

Like indexOf & startsWith, endsWith also accepts an index.

```javascript
'abc.gif'.length; // 7
'abc.gif'.endsWith('.g', 5); // true
```
