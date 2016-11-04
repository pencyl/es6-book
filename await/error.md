# Error with Await and Async

We can leverage try and catch to make out error handling neater with await and async

```javascript
async function myFunc() {
    return await promiseFunc()
        .then(data => data)
        .catch(err => console.log(err))
}

//Same as

async function myFunc() {
    let data = {};
    try {
        data = await promiseFunc();
    } catch (err) {
        console.log(err);
    }
    return data;
}

```

Try and catch will report an errors thrown by our awaited promise.
