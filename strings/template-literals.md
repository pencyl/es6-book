# String template literals

<div class="spec es6">ES6</div>


Template literals allow us to have multi line strings and use expressions & variables within a string.

Think of them as better strings.

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
var name = 'Mike';
var welcomeMessage = 'Welcome, ' + name + '.'; // 'Welcome, Mike.'
```

Converting to a template literal and wrapping our variables in `${}` allows us to use them inline
```javascript
var name = 'Mike';
var welcomeMessage = `Welcome ${name}.`; // 'Welcome, Mike.'
```

They can also be expressions
```javascript
`5 x 5 is ${5 * 5}`; // '5 x 5 is 25'
```

Which can also be a call to a function
```javascript
function multiply (a, b) { return a * b; }
`2 x 2 is ${multiply(2, 2)}`; // '2 x 2 is 4'
```

## Examples

##### Logging
```javascript
logger.info(`${req.method} request ${req.id} received at ${req.path}`);
```

##### Character Escaping

In a single quoted string you'd have to escape single quotes using a backslash
```javascript
'That\'s annoying'
```

In a double quoted string you'd have to escape single quotes using a backslash
```javascript
"\"The beauty of me is that I’m very rich.\" - Donald Trump"
```

In the real world, you are rarely going to need to escape a backtick, which should make your life a little easier. Strings like the below would be much easier to find with grep/ your editor of choice.

```javascript
describe(`/api/blah shouldn't return a 404`, ...
```

##### Templating
Whilst there's [thousands](https://libraries.io/search?platforms=NPM&q=templating) of better ways to do this. You could use it for basic templating without any additional dependencies...
```javascript
const tmpl = names => `
    <table>
        ${names.map(function(name) {
            return `<tr><td>${name.first}</td></tr><tr><td>${name.last}</td></tr>`
        }).join('')}
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

## Should they replace strings?

What you prefer is up to you. They're still a new feature, so it might be clearer to just use them as and when you need them.
