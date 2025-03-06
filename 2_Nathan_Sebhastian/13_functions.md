# 13 - Functions in JavaScript

A function is simply a section (or a block) of code that's written to perform a specific task.

For example, the type casting function `String()` is used to convert data of another type to a string.

The `console.log()` and various array methods we've learned in previous chapters are also functions. But because these functions are called from an object, they are called methods.

You'll learn more about methods later in Chapter 14. For now, just know that a function and a method are essentially the same, except that a method is called from an object.

Besides the built-in functions provided by JavaScript, you can also create your own function.

## How to create your own function

Creating a function starts with typing the `function` keyword followed by the function name, a pair of round brackets, and then a pair of curly brackets.

Here's an example:

```javascript
function greet() {
  // function body here
  console.log("Hello!");
}
```

To call a function, you need to specify the function name followed by parentheses:

```javascript
greet(); // Hello!
```

The code inside the function is executed when you call that function.

## Function parameters and arguments

Parameters are variables used to accept inputs given when the function is called.

You can specify parameters in the function header, inside the parentheses.

The following example shows a function that has one parameter called `name`:

```javascript
function greet(name) {
  // function body
}
```

How you use that `name` parameter inside the function is up to you.

You can use the parameter inside the `console.log()` function as follows:

```javascript
function greet(name) {
  console.log(`Hello, ${name}!`);
  console.log("Nice weather today, right?");
}
```

Now whenever you need to call the `greet()` function, you need to pass an input to fill for the `name` parameter.

The input you passed to fill a parameter is called an argument, and here's how to do it:

```javascript
greet("Peter");
```

The `'Peter'` string inside the parentheses when calling the `greet()` function will be passed as the `name` parameter.

Run the code to receive this output:

```text
Hello, Peter!
Nice weather today, right?
```

You can have more than one parameter when defining the function, but you need to split each parameter with a comma as follows:

```javascript
function greet(name, weather) {
  console.log(`Hello, ${name}!`);
  console.log(`It's ${weather} today, right?`);
}

greet("Nathan", "rainy");
```

Output:

```text
Hello, Nathan!
It's rainy today, right?
```

When you specify two parameters in the function header, you need to pass two arguments. If you call the function without passing the arguments then the value will be `undefined`.

## Default parameters

When defining a function, you can set a default value for any parameter in that function.

For example, the `name` parameter in the function below is a default parameter:

```javascript
function greet(name = "Nathan") {
  console.log(`Hello, ${name}!`);
  console.log("Nice weather today, right?");
}
```

Here, the default value `'Nathan'` will be used when no value or `undefined` is passed for the `name` parameter.

You can test this by calling the `greet()` function without an argument as follows:

```javascript
greet();
greet("Jack");
```

Output:

```text
Hello, Nathan!
Nice weather today, right?

Hello, Jack!
Nice weather today, right?
```

## The return statement

A function can also have a `return` statement inside the code block. A `return` statement is used to return a value back to the caller.

For example, the following function returns the sum of two values:

```javascript
function sum(a, b) {
  return a + b;
}

let result = sum(3, 2);
console.log(result); // 5
```

## Variable scope

A variable declared inside a function can only be accessed from that function. This is because that variable has a local scope.

On the other hand, a variable declared outside of any block is known as a global variable because of its global scope.

These two scopes are important because when you try to access a local variable outside of its scope, you'll get an error.

## Arrow function

The JavaScript arrow function syntax allows you to write a JavaScript function with a shorter, more concise syntax.

```javascript
const greetings = (name) => {
  console.log(`Hello, ${name}!`);
};

greetings("John"); // Hello, John!
```

## Exercise #7

Write a function named `calculateSquare()` that's used to calculate the area and perimeter of a square shape.

The function accepts one parameter: the side of the square.

The formula to calculate the area is `side * side`, and the formula to calculate the perimeter is `4 * side`.

The output shows the size of the side, the area, and the perimeter as follows:

```text
The square side is 8
The area of the square is 64
The perimeter of the square is 32

