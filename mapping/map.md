# Map

<div class="spec es6">ES6</div>


The Map object is a simple key/value map. It is a formalisation and replacement for a simpler object literal map.

Any value, objects or primitive values can be used as either a key or a value.

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

We can find the size and interrogate the Map.
```javascript
drinks.size; // 3
drinks.has('orange'); // false
drinks.has('coke'); // true
```

We can return the keys and values as an iterator.
```javascript
drinks.keys(); // [coke, pepsi, default] as a Iterator
drinks.values() // ['Coke','Pepsi','Unknown drink!'] as a Iterator;
```

We can also iterate of the keys and values with forEach().
```javascript
drinks.forEach((value, key) => {
    console.log(value, key)
});
```

Finally, we can clear the map of one or all values
```javascript
drinks.delete('coke');
drinks.clear();
```

## Objects as keys

The biggest advantage map brings is being able to use objects as keys.

We can rewrite our drinks map to show the advantages, we'll use the key to set an object with an `id` and a `type` and the value with be the ingredients...

```javascript
const drinks = new Map();
var coke = { id: 'coke', type: 'drink' };
var water = { id: 'water', type: 'drink' };

drinks.set(coke, ['Sugar', 'Water', 'Other']);
drinks.set(water, ['Water']);

[...drinks.keys()]; // [{ id: 'coke', type: 'drink' }, { id: 'water', type: 'drink' }];

drinks.get(coke); // ["Sugar", "Water", "Other"]
```
