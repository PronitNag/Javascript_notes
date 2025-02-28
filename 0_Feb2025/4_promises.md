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

✔ JavaScript is single-threaded but uses the Event Loop to handle asynchronous tasks.
✔ Promises do not block execution; they execute their callbacks only when the task is completed.
✔ Other code continues to run normally, ensuring the program remains fast and responsive.

```javascript
console.log("Start");

let myPromise = new Promise((resolve, reject) => {
    resolve("Promise Resolved!"); // Resolving immediately
});

myPromise.then(result => {
    console.log(result); // Runs asynchronously
});

console.log("End");
```

##### output

Start
End
Promise Resolved!

"Start" is logged.
A new Promise is created and resolved immediately, but its .then() callback is placed in the microtask queue.
"End" is logged.
Only after all synchronous code finishes, the JavaScript engine picks up the microtask (.then()) and executes it.
"Promise Resolved!" is finally logged.

## ✔ Execution Flow in JavaScript
When JavaScript encounters an asynchronous task like a Promise or setTimeout(), it follows these steps:

1️⃣ Call Stack:

Executes synchronous code first.
If it finds an asynchronous task, it sends it to the Web APIs.
2️⃣ Web APIs:

If it’s a Promise, it gets resolved/rejected and moves to the Microtask Queue.
If it’s a setTimeout(), it waits in the Web API for the specified time.
3️⃣ Queues:

Microtask Queue: Holds resolved/rejected promises (.then() or .catch()).
Callback Queue: Holds setTimeout(), event listeners, etc.
4️⃣ Event Loop:

First, it checks the Microtask Queue and moves the first task to the Call Stack.
Then, if the Microtask Queue is empty, it moves a task from the Callback Queue to the Call Stack.
This ensures Promises are always executed before setTimeout()

