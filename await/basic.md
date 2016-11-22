# Basic Await and Async

<div class="spec es7">ES7</div>

Likely of ES7, available Edge and Firefox (currently Stage-3).

Async and Await are keywords used in tandem to help make Promises asynchronous and more predictable.

First a quick recap on Promises.

```javascript
import request from 'request';

function getAddress () {
    return new Promise((resolve, reject) => {
        request('https://anyaddress.com/api/get', (err, res, body) => {
            if (err) {
                reject(err); return;
            }
            resolve(body);
        });
    });
}
```

We instantiate a new *Promise* and then *resolve* or *reject* dependent on the result from the XHR request.

```javascript
getAddress()
    .then(data => {
        count : data.length,
        result : data
    })
    .catch(err => console.error(err));
```

We can then leverage the *then* and *catch* method to cleanly deal with results from out XHR request. We avoid callback nesting.

We can also group our promises.

```javascript
function multiAddresses() {
    return Promise.all([getAddress(), getAddress(), getAddress()]);
}

multiAddresses()
    .then(data => {
        count : data.length,
        results : data
    })
    .catch(err => console.error(err));
```

This will return all our requests or will catch an error if any fails.

### Using Async and Await

```javascript
async function asyncFunc () {
    const address = await getAddress()
        .then(data => {
            count : data.length,
            result : data
        })
    return address;
}
asyncFunc().then(data => console.log(data.result));
```

Note that await may only be used in functions marked with the async keyword. Similarly to generators, suspending execution in your context until the promise settles. If the awaited expression isn’t a promise, its casted into a promise.

### Chaining Async functions

```javascript
async function asyncFunc1 () {
    return await asyncFunc2()
        .then(data => data)
}

async function asyncFunc2 () {
    return await getAddress()
        .then(data => {
            count : data.length,
            result : data
        })
}

asyncFunc1().then(data => console.log(data.result));
```

Async functions will return an Promise, so we can chain async functions and know they will run syncronously. This is very useful if you are relying on the returned results to build future queries.
