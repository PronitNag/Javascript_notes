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

