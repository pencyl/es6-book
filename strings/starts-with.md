# String.prototype.startsWith

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
