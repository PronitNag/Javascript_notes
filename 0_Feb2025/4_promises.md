# All about promises

In JavaScript, Promise is a predefined class that is used to handle asynchronous operations. When you create a promise using new Promise(), it takes a function (known as the executor function) with two parameters:

resolve → Call this function when the operation is successful.

reject → Call this function when the operation fails.

```javascript
let myPromise = new Promise((resolve, reject) => {
    // Some asynchronous operation
    let success = true; // Change this to false to see rejection

    if (success) {
        resolve("Operation was successful!");
    } else {
        reject("Operation failed!");
    }
});
```
The Promise constructor (new Promise()) is used to create a promise.

Inside the executor function, we either call resolve() (if the operation succeeds) or reject() (if it fails).

The promise object returned by new Promise() will be in one of three states:

Pending → Initial state, before resolution or rejection.

Fulfilled → If resolve() is called.

Rejected → If reject() is called.

## Handling the promise

```javascript
myPromise
.then(result => {
    console.log("Success:", result);
})
.catch(error => {
    console.log("Error:", error);
});
```

.then() runs when resolve() is called.

.catch() runs when reject() is called.



