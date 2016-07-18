# Generators with Promises

A generator function can use yeild and next() to deal with promises (most likely xhr requests).

```javascript
function getNumber() {
    const get = new Promise((resolve, reject) => {
        setTimeout(() => resolve(Math.random()), 500);
    }).then((data) => {
        theNumber.next(data);
    });
}

function *showNumber() {
    const num1 = yield getNumber();
    const num2 = yield getNumber();
    const num3 = yield getNumber();
    console.log(`sum equals ${num1 + num2 + num3}`);
}

const theNumber = showNumber();
theNumber.next();
```

We wait for all the promises to resolve before we sum the total of the numbers.

> **Promises** are now standard in ES6.