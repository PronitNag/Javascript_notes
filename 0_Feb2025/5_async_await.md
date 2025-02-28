# All about Async and await

Crucial facts about the relation between promises and async/await:

1) async function returns promise
   
2) await waits for promise to resolve( await pauses execution until the promise resolves ).

## Fetching Data with async/await

```javascript
async function fetchData() {
    let response = await fetch("https://jsonplaceholder.typicode.com/todos/1");
    let data = await response.json();
    console.log(data);
}

fetchData();
```

await fetch(url) waits for the response from the server. <br />
await response.json() waits for the response to be converted into JSON.<br />
The parsed data is then logged to the console. <br />

## 🔹 Key Points to Remember

async function always returns a Promise. <br />
await can only be used inside async functions (unless using top-level await in modern JS). <br />
Makes asynchronous code easier to read and write. <br />
Handles Promises without using .then() and .catch().<br />

## what do you mean when you write async to a function does this mean that the function leaves the call stack and goes to Web Api and then to queue?

we will break down the question and solve it 

### 🔹 What Happens When You Write async Before a Function?

When you write async before a function, it does NOT mean the function automatically goes to the Web API or Task Queue. Instead, it does two things:

Makes the function always return a Promise (even if you return a normal value).<br />
Allows the use of await inside it, pausing execution until the awaited promise resolves.<br />

### 🔹 Does an async Function Leave the Call Stack?

No, just declaring a function as async does nothing special.<br />
The function runs like a normal function until it reaches an await.<br />
If there's an await, the function pauses, allowing the event loop to continue with other tasks.<br />

### 🔹 Execution Flow: Does It Go to Web API and Task Queue?

**It depends on whether the function uses Web APIs or not.**

### ✅ Case 1: No Web API Involved (Promise.resolve())?

```javascript
async function test() {
    console.log("1. Start");
    let result = await Promise.resolve("2. Resolved");
    console.log(result);
    console.log("3. End");
}

test();
console.log("4. Outside function");
```

**output**

1. Start<br />
4. Outside function<br />
2. Resolved<br />
3. End<br />

## Result

console.log("1. Start") runs normally. <br />
await Promise.resolve("2. Resolved") pauses execution (but does NOT go to Web API or Task Queue).<br />
The function execution is put on microtask queue while the rest of the script runs.<br />
Once the main script finishes, it resumes execution and logs "2. Resolved"<br />

### ✅ Case 2: Web API Involved (fetch())?

```javascript
async function fetchData() {
    console.log("1. Start fetching");
    let response = await fetch("https://jsonplaceholder.typicode.com/todos/1");
    let data = await response.json();
    console.log("2. Data received:", data);
}

fetchData();
console.log("3. Outside function");
```

#### output

1. Start fetching<br />
3. Outside function<br />
2. Data received: { todo object }<br />

📌 What happens?

console.log("1. Start fetching") runs. <br />
fetch() is a Web API, so it is sent to the browser Web API environment. <br />
The function pauses at await fetch(), allowing the event loop to continue. <br />
"3. Outside function" prints while waiting for the fetch request to complete. <br />
Once fetch() finishes, the response is moved to the Task Queue. <br />
The event loop picks it up and resumes function execution. <br />

### 🔹 How Can Multiple Functions Exist in the Call Stack?

The call stack only executes one function at a time, but when an async function is paused, other functions can enter the stack.<br />
When an await is hit, the function pauses and is removed from the call stack while waiting for a Promise to resolve.<br />
Meanwhile, other functions continue executing.<br />
Once the awaited function resumes, it is pushed back onto the call stack.<br />


### Sure! Let's see how an async function without await behaves in the JavaScript event loop.

```javascript
async function test() {
    console.log("1. Start");
    return "2. Resolved"; // No await, so it returns a Promise immediately
}

console.log("3. Before calling function");

let result = test(); // Calling the async function

console.log("4. Function called");

result.then(console.log); // Handling the returned Promise

console.log("5. End of script");
```

#### output

3. Before calling function<br />
1. Start<br />
4. Function called<br />
5. End of script<br />
2. Resolved<br />

🔹 Execution Flow<br />

"3. Before calling function" is printed.<br />
test() is called, "1. Start" is printed.<br />
Since there is no await, test() immediately returns a Promise.<br />
"4. Function called" is printed.<br />
"5. End of script" is printed.<br />
The .then(console.log) is in the microtask queue, so "2. Resolved" prints at the end.<br />

### Great! Now let’s wrap the same code inside another await function and see how it behaves.

```javascript
async function test() {
    console.log("1. Start");
    return "2. Resolved"; // No await, so it returns a Promise immediately
}

async function main() {
    console.log("3. Before calling function");

    let result = await test(); // Using await

    console.log("4. Function called");
    console.log(result); // Logging the resolved value

    console.log("5. End of script");
}

main();
console.log("6. Outside function");
```

output:

3. Before calling function<br />
1. Start<br />
6. Outside function<br />
4. Function called<br />
2. Resolved<br />
5. End of script<br />

🔹 Execution Flow

1. "3. Before calling function" is printed.
2. main() is called, but since it's async, it starts execution and does not block the script.
3. Inside main(), test() is called, printing "1. Start".
4. test() returns a Promise, so await test(); pauses execution of main().
5. While main() is paused, the event loop continues, and "6. Outside function" is printed.
6. Once test() resolves, await test(); resumes execution.
7. "4. Function called" is printed.
8. The resolved value "2. Resolved" is printed.
9. "5. End of script" is printed last.
