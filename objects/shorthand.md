# Property shorthand

You've probably written code that assigns properties using variables of the same name before.

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
  url
}).then(...)
```
