# Map

<div class="spec es6">ES6</div>


The Map object is a simple key/value map. It is a formalisation and replacement for a simpler object literal map.

```javascript
function getDrink(type) {
    const drinks = {
        'coke': 'Coke',
        'pepsi': 'Pepsi',
        'default': 'Unknown drink!'
    };
    return drinks[type] || drinks['default'];
}
getDrink('coke'); // Coke
getDrink('orange'); // Unknown drink!
```

This is a simple object map for selecting a drink name. We can replace the same functionality with:

```javascript
function getDrink(type) {
    const drinks = new Map();
    drinks.set('coke','Coke');
    drinks.set('pepsi','Pepsi');
    drinks.set('default','Unknown drink!');
    return drinks.get(type) || drinks.get('default');
}
getDrink('coke'); //Coke
getDrink('orange'); //Unknown drink!
```

The advantage to Map() is that it offers a number of methods that aid with its use.

```javascript
drinks.size; // 3
drinks.has('orange') //false
drinks.has('coke') //true
```

We can find the size and interrogate the Map.

```javascript
drinks.keys(); // [coke,pepsi,default] as a Iterator
drinks.values() // ['Coke','Pepsi','Unknown drink!'] as a Iterator;
```

We can return the keys and values as an iterator.

```javascript
drinks.forEach((value,key) => {
    console.log(value,key)
});
```

We can also iterate of the keys and values with forEach().

```javascript
drinks.delete('coke');
drinks.clear();
```

Finally, we can clear the map of one or all values

> **WeakMap()**

> A WeakMap() is the same as a Map() but the values can be garbage collected for better memory management. That means that you can associate data with objects without having to worry about memory leaks.

> You can’t iterate over the contents – neither the keys, nor the values, nor the entries. You can’t clear a WeakMap, either.
