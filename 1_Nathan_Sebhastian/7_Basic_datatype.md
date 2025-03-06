# 7 - JavaScript Basic Data Types

Data Types are simply definitions for different types of data known to a programming language.

A data type contains specifications about what you can and can't do with that data.

To show you a brain-friendly example, I'm sure you agree that 2 + 2 = 4?

Well, JavaScript also agrees with that:

```javascript
console.log(2 + 2);
// Output: 4
```

But what if you try to add a number with letters as shown below?

```javascript
console.log(2 + "ABC");
```

**Output:**

```
2ABC
```

Adding a number and letters together will cause JavaScript to concatenate or join the values together.

In this section, you're going to learn basic data types that JavaScript knows:

- Strings
- Numbers
- Booleans
- Null
- Undefined

You will also see how these different types react to operators such as `+` shown in the above example.

## Strings in JavaScript

Strings are simply data defined as a series of characters.

You've seen an example of string data previously when you call the `console.log()` function to print a message:

```javascript
let message = "Hello, Sunshine!";
console.log(message); // Hello, Sunshine!
```

A string needs to be enclosed in quotations. You can use double quotes or single quotes, but they have to match.

You'll get an error when you use different quotation marks like this:

```javascript
// Invalid or unexpected token
let message = "Hello';
```

You can join two or more strings as one with the plus `+` symbol. Don't forget to add a space before the next string or you'll get a string without spaces!

```javascript
let message = "Hello " + "and " + "Goodbye!";
console.log(message);

// Output: Hello and Goodbye!
```

When printing a variable's value, you can also add strings in the `console.log()` function directly as follows:

```javascript
let message = "Hello, Dave!";
console.log("The message is: " + message);

// Output: The message is: Hello, Dave!
```

This is particularly useful when you have multiple strings to `console.log` in one sentence as follows:

```javascript
let name = "John";
let topic = "JavaScript";

console.log(name + " is learning " + topic + " today");

// Output: John is learning JavaScript today
```

Or you can also use the template strings format, which allows you to embed a variable directly inside the string as follows:

```javascript
let name = "John";
let topic = "JavaScript";

console.log(`${name} is learning ${topic} today`);

// Output: John is learning JavaScript today
```

To use the template strings format, you need to use the backtick (`` ` ``) character to wrap the string instead of quotations.

The variable is embedded in the string using the dollar symbol and curly brackets as in `${variable}`.

This way, JavaScript knows that you're referencing a variable inside the string.

When you have multiple strings to print in a single line, then the template strings format is more convenient because you didn't have to break the string with quotations and concatenations.

Next, strings can also represent numbers. You surround the numbers in quotations as follows:

```javascript
let score = "10" + "30";
console.log(score);

// Output: 1030
```

When you join two string numbers with a `+` symbol, JavaScript will join the two numbers instead of performing arithmetic addition.

This is how strings work in JavaScript. Let's look at numbers next.

## Numbers (integers and floats) in JavaScript

Number data types represent different kinds of numbers. There are two types of numbers in JavaScript:

- Integers
- Floats

An integer is a whole number without decimals and fractions. Below, you see examples of two integers `x` and `y`:

```javascript
let x = 1;
let y = 2;

console.log(x + y);

// Output: 3
```

On the other hand, floats refer to numbers with decimal points like this:

```javascript
let f = 1.2;
let z = 2.35;

console.log(f + z);

// Output: 3.55
```

To create a float, you need to write a number and use `.` to define the decimal values.

With number types, you can perform arithmetic operations such as addition `+`, subtraction `-`, division `/`, and multiplication `*` just like how you use a calculator.

## Booleans in JavaScript

Boolean is a type that represents `true` and `false` values.

You can think of Booleans as a light switch that can only be in one of two positions: on or off.

So it is with Boolean values in programming languages. They are used when JavaScript needs to make a decision: Go left or go right? Right or wrong?

Here's how you create Boolean values in JavaScript:

```javascript
let on = true;
let off = false;
```

This data type is frequently used when you need to make a decision using a control flow. You'll see why Boolean values are very useful in developing a program later in Section 9.

## Undefined in JavaScript

`Undefined` is a data type in JavaScript used to represent a variable that hasn't been assigned any value yet.

Anytime you declared a variable without assigning any value, the `undefined` value will be assigned to that variable. For example:

```javascript
let first_name;
console.log(first_name); // undefined
```

You can also assign `undefined` to a variable explicitly as follows:

```javascript
let last_name = undefined;
```

But this is usually not recommended, because JavaScript has another value called `null` which is used to mark a variable as empty.

## Null in JavaScript

The `null` value is a special data type that represents an empty or unknown value. Here's how you assign a variable as `null`:

```javascript
let first_name = null;
```

The code above means that the value of `first_name` is empty or unknown.

At this point, you may be thinking what's the difference between `undefined` and `null`? They seem to serve a similar purpose.

And you are correct. Both `undefined` and `null` are values that represent nothing, and other programming languages usually only have one, and that is `null`.

In JavaScript, the `undefined` value is reserved as the default value when a variable is declared, while `null` means you intentionally assign an "empty" value for the variable.

This slight difference will come to play later when you learn about functions in Chapter 13.

For now, just keep in mind that JavaScript treats `undefined` as the "default" empty value and `null` as the "intentional" empty value.

