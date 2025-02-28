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


