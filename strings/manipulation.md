# String manipulation methods

ES6 introduces some new methods to strings that can be very useful and replace unintuitive code.

## startsWith

Checking a string starts with something is a fairly common task.

Currently you can check a string starts with something using `.indexOf()`

```javascript
'https://blah.com'.indexOf('https') === 0; // true
'http://blah.com'.indexOf('https') === 0; // false
```

There's a caveat though, what if the string we're testing exists more than once?

```javascript
function isGoogleUrl (url) {
  return url.indexOf('google.com') === 0;
}

isGoogleUrl('http://google.com?referrer=google.com'); // false
```

In this example, the indexOf 'google.com' is 7.

Now we can use the built in startsWith method making this a bit more reliable and more readable, our intent in much clearer.

```javascript
'https://blah.com'.startsWith('https'); // true
```

Like indexOf, startsWith accepts an index. We could easily ignore the first 1/2 characters by passing in an index

```javascript
'https://blah.com'.startsWith('blah', 8); // true
```

## endsWidth

Again, you can check a string ends with something using indexOf...

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

## includes

Includes is self explanatory, you can check if a string contains another string.

```javascript
'Hello Dave'.includes('Dave'); // true
```


## repeat

Repeat can be quite handy, it allows you to repeat a string n times.

```javascript
'test'.repeat(10); // 'testtesttesttesttesttesttesttesttesttest'
```
