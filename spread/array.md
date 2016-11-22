##Array Spread

<div class="spec es6">ES6</div>

Array spread allows us to do work on arrays that previously need to us Array methods(). It is a shorthand way to deal with common array manipulations.

```javascript
const parts = ['shoulders', 'knees'];

//same as unshift
const lyricsFirst = [...parts, 'toes'];
//['shoulders','knees','toes']

//same as push()
const lyricsLast = ['toes', ...parts];
//['toes','shoulders','knees']

//same as splice()
const lyricsMiddle = ['head', ...parts, 'and', 'toes'];
//['head','shoulders','knees,'and','toes']

//Same as concat()
const bones = ['spine', 'skull']
const grissle = [...bones, ...parts];
//['spine','skull','shoulders','knees']
```

We can also convert array-like objects to arrays:

```javascript
[...iterator] //convert iterator to array
[arguments] //convert arguments to array
```

This returns a new array.
