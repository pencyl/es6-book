# Destructuring

Destructuring assignments give us a much cleaner way of extracting values from objects.

```javascript
var { a, b } = { a: 10, b: 20 };
console.log(a, b); // 10, 20
```

### Assigning to different variable names
```javascript
var { a: hello, b } = { a: 10, b: 20 };
console.log(hello); // 10
```

### Default values
Just like with arrays we can still use default values incase a value is missing.

```javascript
var { a, b, c=0 } = { a: 10, b: 20 };
console.log(a, b, c); // 10, 20, 0
```

### Nested objects
```javascript
var request = {
  path: '/endpoint',
  url: '/endpoint?a=b',
  query: 'search=xyz',
  params: {
    search: 'xyz'
  }
};

var { params: {search: searchQuery} } = request;
console.log(searchQuery); // xyz
```
