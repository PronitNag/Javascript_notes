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
