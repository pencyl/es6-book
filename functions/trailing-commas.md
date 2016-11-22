# Trailing commas in function parameters & calls

This [proposal](https://github.com/tc39/proposal-trailing-function-commas) is now stage 4, expected to be published in 2017/ES2017. So to use it you will need to use the [ES2017 Babel preset](https://www.npmjs.com/package/babel-preset-es2017).


The indention of this proposal is to allow trailing commas in function calls and definitions when JavaScript is written in this specific style...

It's not life changing and you may not agree with the style, but, it's a good example of an accepted proposal to the spec.

```javascript
function helloWorld(
  one,
  two
) { return one + two }

helloWorld(
  1,
  2
); // 3
```

It might look a bit odd, but this is a valid way to define and call functions. However, with the above example, renaming or adding a parameter can result in a fuzzy diff with git.

Lets add a third parameter...

```diff
 function helloWorld(
   one,
-  two
+  two,
+  three
 ) { return one + two }

 helloWorld(
   1,
-  2
+  2,
+  3
 );
```

We've only added a parameter and the argument to go with it, but in total 4 lines have been added and 2 removed.

If the function was defined with trailing commas, it would just be a two line change...

```diff
 function helloWorld(
   one,
   two,
+  three,
 ) { return one + two }

 helloWorld(
   1,
   2,
+  3,
 );
```






> There's also a [babel preset](https://www.npmjs.com/package/babel-plugin-syntax-trailing-function-commas) specifically for this feature if you want to be more specific or not include the entire 2017 spec in your preset
