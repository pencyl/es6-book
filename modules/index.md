# Modules

Prior to ES6 there were numerous ways of modularizing JavaScript code. The two most common are

### Asynchronous Module Definition (AMD)
[RequireJS](http://requirejs.org/) standard, mainly used for asynchronous loading in browsers.

```javascript
define(function (require) {
    require(['a', 'b'], function (a, b) {
        // modules a and b are now available for use
    });
});
```

### CommonJS Modules
More compact, mostly used with [Node.js](https://nodejs.org/api/modules.html) on the server, loading synchronously.

```javascript
const a  = require('a');
const b  = require('b');
// modules a and b are synchronously loaded
```

## ES6 modules *The final syntax*
The goal for ES6 was to have modules that serve both of the above use cases. Using a module loader that's built into the language also allows for extra features that wouldn't of been possible like static analysis and as they're a first class feature the syntax is even more compact.

AMD & CommonJS modules aren't going away any time soon.

If your code is ES6 it should be safe to refactor to use imports with existing CommonJS modules.

If you were to make a module to be published on npm today and you wanted it to be consumed by as many node versions as possible, you might want to consider sticking with the old CommonJS exports.


## Examples

### Importing for side effects
This is used a lot within React
```javascript
import 'react'; // React does it's magic, we can't refer to it
```

### Default

```javascript
/* myModule.js */
export default function () {
	return 'boo!'
}
/* end myModule.js */

import myModule from 'myModule';
console.log(myModule()); // boo!
```

### Named member
A "member" being something that was exported within the module
```javascript
/* myModule.js */
export const greeting = 'hello';
/* end myModule.js */

import { greeting } from 'myModule';
console.log(greeting); // hello
```

> Imported const's will have slightly more protection than a normal const. Webpack will throw a SyntaxError when trying to build if you try to reassign an imported variable

### Renamed member
With a similar syntax to export, specific members can be renamed for use locally.
```javascript
/* myModule.js */
export const pi = 3.14;
/* end myModule.js */

import { pi as pie } from 'myModule';
console.log(pie); // 3.14
```


### Multiple members

```javascript
/* myModule.js */
export const greeting = 'hello';
export const sendOff = 'cya';
export function greet(name) {
	return greeting + ' ' + name;
};
/* end myModule.js */

import { greet, greeting, sendOff } from 'myModule';
console.log(greeting); // hello
console.log(sendOff); // cya
console.log(greet('Matt')); // hello
```

### Multiple members, imported at a namespace

```javascript
/* myModule.js */
export const greeting = 'hello';
export const sendOff = 'cya';
export function greet(name) {
	return greeting + ' ' + name;
};
/* end myModule.js */

import { * as greetingStuff } from 'myModule';
console.log(greetingStuff.greeting); // hello
console.log(greetingStuff.sendOff); // cya
console.log(greetingStuff.greet('Matt')); // hello
```

### Default & other members
```javascript
/* myModule.js */
export const greeting = 'hello';
export const sendOff = 'cya';
export default function greet(name) {
	return greeting + ' ' + name;
};
/* end myModule.js */

import myModule, { sendOff } from 'myModule';
console.log(sendOff); // cya
console.log(myModule('Matt')); // hello
```
