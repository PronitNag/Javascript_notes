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

the function that is inserted as argument are called as callbacks.

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

**The parameter that is passed is stored as a local variable and that is called**

The doSomething() function, which is created with the parameter callback, is just calling whatever function is being passed in as an argument.

### Give a exapmle of callbacks with real life use??

```javascript
function judge(grade) {
    switch (true) {
        case grade == "A":
            console.log("You got an", grade, ": amazing!");
            break;
        case grade == "B":
            console.log("You got a", grade, ": well done!");
            break;
        case grade == "C":
            console.log("You got a", grade, ": alright.");
            break;
        case grade == "D":
            console.log("You got a", grade, ": hmmm...");
            break;
        default:
            console.log("An", grade, "! What?!");
    }
}

function getGrade(score, callback) {
    let grade;
    switch (true) {
        case score >= 90:
            grade = "A";
            break;
        case score >= 80:
            console.log(score);
            grade = "B";
            break;
        case score >= 70:
            grade = "C";
            break;
        case score >= 60:
            grade = "D";
            break;
        default:
            grade = "F";
    }
    judge(grade);
}

getGrade(85, judge);
```

we call the `getGrade()` with two arguments 85 and the function `judge()`

The judge() function gets stored in a callback. After determining the grade, the function that is stored in a callback (judge() in this case) gets called with the grade. think as first the student gets the score and then think judge as report card.

Real life example is that > when one function is still waiting for the results of a call to the database before calling the callback function that is going to process the data.


