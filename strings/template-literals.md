# String template literals

Template literals allow us to have multi line strings and use expressions & variables within a string.

To create a template literal, it must be enclosed in a "backtick", instead of quotes or double quotes.

```javascript
var oldString = "hi";
var newString = `hi`;
```

> If you ever need to use a backtick within your template literal, you can escape it with a backslash before the backtick.

## Multi line strings

No extra syntax is required to do multi line strings, once it's a template literal you can just add new lines...

Before...
```javascript
var multiLineString = 'line one of a string' +
  'blah' +
  'blah' +
  'blah' +
  'blah'
```

Now...
```javascript
var multiLineString = `line one of a string
blah
blah
could stick a whole book in here
blah
blah`
```

> If your editor doesn't support ES6, syntax highlighting with multi line strings is going to start to break up.
> We've covered syntax highlighting in [further reading](/reference)

## Expressions

With a template literal we can now use variables or expressions inline without string concatenation.

Before...
```javascript
var welcomeMessage = "Welcome, " + name + ".";
```

Converting to a template literal and wrapping our variables in `${}` allows us to use them inline
```javascript
var welcomeMessage = `Welcome ${name}.`;
```

They can also be expressions
```javascript
console.log(`5 x 5 is ${5 * 5}`);
```

Which can also be a call to a function
```javascript
function multiply (a, b) { return a * b; }
console.log(`5 x 5 is ${multiply(5, 5)}`);
```

## Examples

Logging
```javascript
logger.info(`${req.method} request ${req.id} received at ${req.path}`);
```

No longer having to escape singlequotes whenever you use a contraction
```javascript
describe(`myFunc shouldn't throw an error`, ...
```

"Templating", whilst there's [thousands](https://libraries.io/search?platforms=NPM&q=templating) of better ways to do this. You could
```javascript
const tmpl = names => `
  <table>
  ${names.map(name => `
      <tr><td>${name.first}</td></tr>
      <tr><td>${name.last}</td></tr>
  `).join('')}
  </table>`;

const data = [
  { first: 'Matt', last: 'Tortolani' },
  { first: 'Callum', last: 'Rimmer' },
];

tmpl(data);
// <table>
//   <tr><td>Matt</td></tr>
//   <tr><td>Tortolani</td></tr>
//
//   <tr><td>Callum</td></tr>
//   <tr><td>Rimmer</td></tr>
// </table>
```
