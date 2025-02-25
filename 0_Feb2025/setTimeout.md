# How to use setTimeOut method

```javascript

    setTimeout(hello, 1000);
       
    function hello(){
          console.log("Hello");
    }


    setTimeout(function() {
    console.log("Hello");
    }, 1000);

    setTimeout(() => console.log("Hello"), 1000);

    setTimeout(() => {
      console.log("Hello")
    }, 1000);
```


Q. Does setTimeout takes a callback function?
A  yes

### what is a callback function?

A callback function is a function that is passed as an argument to another function and is executed later

`setTimeout(hello, 1000);`


### Give me a simplest example of callback function and expaling callback in a different style?

``` javascript
function doSomething(callback) {
 callback();
}

function sayHi() {
   console.log("Hi!");
}

doSomething(sayHi);
```

It is just a function that takes another function as an argument, which is then called when the rest of the initial function has finished.

The doSomething() function, which is created with the parameter callback, is just calling whatever function is being passed in as an argument.

###
