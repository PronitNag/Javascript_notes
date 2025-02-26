# Give a example of callback hell with explaining the code

```javascript

    setTimeout(()=>{
      console.log("Hello");
      setTimeout(()=>{
        console.log("Good");
        setTimeout(()=>{
          console.log("Morning");
        },1000);
      },4000);
    },5000);

```

Each setTimeout is nested inside another, making it harder to read and maintain. If you had to great good afternoon and more( I mean events), the indentation would get out of control!

Debugging becomes difficult as each function is dependent on the previous one.

Hello will me printed after 5 seconds, Good after 4 seconds and Morning after 1 seconds.

We can write the above code with 

```javascript
function sayHello(callback) {
    setTimeout(() => {
        console.log("Hello");
        callback();
    }, 5000);
}

function sayBye(callback) {
    setTimeout(() => {
        console.log("Bye");
        callback();
    }, 4000);
}

function sayHow() {
    setTimeout(() => {
        console.log("How");
    }, 1000);
}

// Callback hell structure
sayHello(() => {
    sayBye(() => {
        sayHow();
    });
});
```
