# Infinite Generator Function

<div class="spec es6">ES6</div>


Generators can be powerful when considering iterables are not finite.

```javascript
function *Stateful(x) {
    while(true) {
        x = x * 2;
        yield x;
    }
}

const state = new Stateful(1);
state.next(); // {value: 2, done: false}
state.next(); // {value: 4, done: false}
state.next(); // {value: 8, done: false}
```

In the above example, notice how the value of x is maintained on every next(). We do not need to manage the value of x outside the generator function like we do with for statements and while loops.

Our generator function has also created a potentially infinite iterable value, we will never reach { done : true }. We have not had to define a huge array to iterate through, it has been created programmatically.
