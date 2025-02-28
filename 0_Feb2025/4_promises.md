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

### How promises run on javascript
✔ JavaScript is single-threaded but uses the Event Loop to handle asynchronous tasks.<br />
✔ Promises do not block execution; they execute their callbacks only when the task is completed.<br />
✔ Other code continues to run normally, ensuring the program remains fast and responsive.<br />

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

### output

Start<br />
End<br />
Promise Resolved!<br />

"Start" is logged.<br />
A new Promise is created and resolved immediately, but its .then() callback is placed in the microtask queue.<br />
"End" is logged.<br />
Only after all synchronous code finishes, the JavaScript engine picks up the microtask (.then()) and executes it.<br />
"Promise Resolved!" is finally logged.<br />

## ✔ Execution Flow in JavaScript
When JavaScript encounters an asynchronous task like a Promise or setTimeout(), it follows these steps:

1️⃣ Call Stack:

Executes synchronous code first.<br />
If it finds an asynchronous task, it sends it to the Web APIs.<br />
2️⃣ Web APIs:

If it’s a Promise, it gets resolved/rejected and moves to the Microtask Queue.<br />
If it’s a setTimeout(), it waits in the Web API for the specified time.<br />
3️⃣ Queues:

Microtask Queue: Holds resolved/rejected promises (.then() or .catch()).<br />
Callback Queue: Holds setTimeout(), event listeners, etc.<br />
4️⃣ Event Loop:

First, it checks the Microtask Queue and moves the first task to the Call Stack.<br />
Then, if the Microtask Queue is empty, it moves a task from the Callback Queue to the Call Stack.<br />
This ensures Promises are always executed before setTimeout()<br />

# What will be the output of this code?

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Inside setTimeout");
}, 0);

Promise.resolve("Inside Promise").then(console.log);

console.log("End");
```

✔ Step-by-Step Execution <br />
1️⃣ "Start" is logged (Synchronous - Call Stack). <br />
2️⃣ setTimeout() moves to Web API, then to Callback Queue.<br />
3️⃣ Promise.resolve() moves to Web API, then to Microtask Queue.<br />
4️⃣ "End" is logged (Synchronous - Call Stack). <br />
5️⃣ The **Microtask Queue runs first**: "Inside Promise" is logged. <br />
6️⃣ The **Callback Queue runs next**: "Inside setTimeout" is logged. <br />

✔ Final Output <br />
Start <br />
End<br />
Inside Promise<br />
Inside setTimeout<br />

## Q. Even if the promise takes 2 seconds and the settimeout take 0 seconds then also?

Ans-> Yes! Even if the Promise takes 2 seconds and the setTimeout() takes 0 seconds, the Promise will still execute first once it's resolved because it belongs to the Microtask Queue, which has higher priority than the Callback Queue

```javascript
console.log("Start");

setTimeout(() => console.log("🥉 Third (setTimeout)"), 0);

new Promise((resolve) => {
    for (let i = 0; i < 2_000_000_000; i++) {} // Simulating 2s delay (blocking)
    resolve("🥈 Second (Promise)");
}).then(console.log);

console.log("End");
```

## output
Start <br />
End <br />
🥈 Second (Promise) <br />
🥉 Third (setTimeout) <br />

> " Think of this as a fetch Api which takes 2 seconds Even if a fetch request takes 2 seconds, it will still execute before a setTimeout(0) because Promises (Microtask Queue) always have higher priority over setTimeout (Callback Queue). "
