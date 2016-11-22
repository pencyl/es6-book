# Destructuring

<div class="spec es6">ES6</div>


Destructuring assignments give us a much cleaner way of extracting values from objects.

Without destructuring
```javascript
var data = { productName: 'Socks', price: 5 };

var productName = data.productName;
var price = data.price;

console.log(productName); // 'Socks'
console.log(price); // 5
```

With destructuring
```javascript
var data = { productName: 'Hat', price: 20 };

var { productName, price } = data;

console.log(productName); // 'Hat'
console.log(price); // 20
```

### Assigning to different variable names
```javascript
var data = { productName: 'Scarf', price: 10 };

var { productName: title, price } = data;

console.log(title); // 'Scarf'
console.log(price); // 10

console.log(productName); // "ReferenceError: productName is not defined
```

### Default values
If you try to destructure and the variable isn't defined. It will return undefined.
```javascript
var data = { productName: 'Belt', price: 50 };

var { productName, price, discount } = data;

console.log(discount);
```

Just like with arrays we can still use default values incase a value is missing.
```javascript
var data = { productName: 'Coat', price: 150 };

var { productName, price, discount = 0 } = data;

console.log(productName); // 'Coat'
console.log(price); // 150
console.log(discount); // 0
```

### Nested objects

```javascript
var data = {
    productName: 'Shoes',
    price: 24,
    stock: {
        store: 4,
        online: 100
    }
};

var { stock: { store } } = data;
console.log(store); // 4

var { stock: { store: inStoreStock } } = data;
console.log(inStoreStock); // 4
```

#### console.log trick

It's fairly common to log the state of a variable like the following

```javascript
const myVar = 124;
console.log('myVar', myVar); // myVar 124
```

With object destructing we can simplify this by logging an object, but not specifying the key name, the variable name will be used.

```javascript
const myVar = 124;
console.log({myVar}); // {myVar: 124}
```

Arguably what is logged to the console isn't as clear, as the object is only there for sake of simplifying the code.

But, this method is less prone to typing errors and shorter to type.
