# Set

<div class="spec es6">ES6</div>


The Set object is similar to Map() but lets you store *unique* values in a list rather than key/values.

```javascript
const drinks = new Set();
drinks.add('coke');
drinks.add('pepsi');

//or

const drinks = new Set(['coke', 'pepsi']);
```

We can find the size and interrogate the Set.

```javascript
drinks.size; // 3
drinks.has('orange'); //false
drinks.has('coke'); //true
```

We can also iterate over the set with a for-of loop or froEach().

```javascript
for(let drink of drinks) {
    console.log(drink);
}

drinks.forEach((drink) => {
    console.log(drink);
})
```

we can convert the set to an array simply using spread operator:

```javascript
let drinksArray = [...drinks];
```

Finally, we can clear the map of one or all values

```javascript
drinks.delete('coke');
drinks.clear();
```

## Uniqueness

So far, this essentially looks like a fancy Array. An important distinction is that a Set only stores *unique* values...

```javascript
const drinks = new Set(['coke', 'pepsi', 'coke', 'pepsi', 'tango']);
console.log([...drinks]); // ["coke", "pepsi", "tango"]
```

<br/>
<br/>
<br/>

> **WeakSet()**
> A WeakSet() is the same as a Map() but the values can be garbage collected for better memory management.

> You can’t iterate over the contents – neither the keys, nor the values, nor the entries. You can’t clear a WeakSet, either.
