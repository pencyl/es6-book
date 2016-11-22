# Async Generator Function

<div class="spec es6">ES6</div>

A generator function can use yield and next() to make async -> sync. This allows queuing of async operations.

```javascript
function firstName() {
    setTimeout(function(){
        hello.next('Don')
    }, 1000);
}

function lastName() {
    setTimeout(function(){
        hello.next('Cheadle')
    }, 1000);
}

function *sayHello() {
    const a = yield firstName();
    const b = yield lastName();
    console.log(a, b); // Don Cheadle
}

var hello = sayHello();
console.log('started');
hello.next();
```

We are creating async operations by using setTimeout() to make a delay. Once firstName() and lastName() return, we console log out the name.
