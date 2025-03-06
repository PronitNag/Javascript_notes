# 8 - Type Conversion and Coercion

At times, you might want to convert one data type into another so that the program runs as expected.

For example, suppose you need to convert a string into an integer so you can perform an addition between numbers.

If you have one of the numbers as a string, JavaScript joins them together instead of adding:

```javascript
let x = "7";
let y = 5;

console.log(x + y); // 75
```

To add the two numbers properly, you need to convert the `x` variable into an integer.

Changing the data from one type to another is also known as **type conversion** or **type casting**. There are 3 functions frequently used to do type conversion:

- `Number()`
- `String()`
- `Boolean()`

As their name implies, these type conversion functions will attempt to convert any value you specified inside the parentheses to the type of the same name.

To convert a string into an integer, you can use the `Number()` function:

```javascript
let x = "7";
let y = 5;

// Convert x to integer
x = Number(x);

console.log(x + y); // 12
```

On the other hand, the `String()` function converts a value of another type to a string. If you type `String(true)`, then you'll get `'true'` back.

Passing a value of the same type as the function has no effect. It will just return the same value back.

## Type coercion

In JavaScript, **type coercion** is a process where a value of one type is implicitly converted into another type.

This is automatically done by JavaScript so that your code won't cause an error. But as you'll see in this section, type coercion can actually cause undesired behavior in the program.

Let's consider what happens when you perform an addition between a number and a string in JavaScript:

```javascript
console.log(1 + "1");
```

As you've seen in the previous section, JavaScript will consider the number as a string and join the two letters as `"11"` instead of adding them (`1 + 1 = 2`).

But you need to know that other programming languages don't respond the same way.

Programming languages like Ruby or Python will respond by stopping your program and giving an error as feedback. It will respond with something along the lines of _"Cannot perform addition between a number and a string"._

But JavaScript will see this and say: _"I cannot do the operation you requested as it is, but I can do it if the number `1` is converted to a string, so I'll do just that."_

And that's exactly what **type coercion** is. JavaScript notices that it doesn't know how to execute your code, but it doesn't stop the program and respond with an error.

Instead, it will change the data type of one of the values without telling you.

While type coercion doesn't cause any errors, the output is actually something you don't want either.

## Type coercion rules

Type coercion rules are never stated clearly anywhere, but I did find some rules by trying various silly code myself.

It seems that JavaScript will first convert data types to string when it finds different data types:

```javascript
1 + "1" // "11"
[1 ,2] + "1" // "1,21"
true + "1" // "true1"
```

But the order of the values matters when you have an object. Writing objects first always returns numeric `1`:

```javascript
{ a: 1 } + "1" // 1
"1" + { a: 1 } // "1[object Object]"
true + { a: 1 } // "true[object Object]"
{ a: 1 } + 1 // 1
```

JavaScript can calculate between boolean and numeric types because boolean values `true` and `false` implicitly have the numeric values `1` and `0`:

```javascript
true + 1 // 1+1 = 2
false + 1 // 0+1 = 1
[1,2] + 1 // "1,21"
```

Type coercion is always performed implicitly. When you assign the value as a variable, the variable type will never change outside of the operation:

```javascript
let myNumber = 1;
console.log(myNumber + "1"); // prints 11
console.log(myNumber); // still prints number 1 and not string
```

You can try to find some more on your own, but you hopefully understand what type coercion is and how it works by now.

## Why you should avoid type coercion

JavaScript developers are generally divided into two camps when talking about type coercion:

1. Those who think it's a **feature**
2. Those who think it's a **bug**

If you ask me, I would recommend that you **avoid using type coercion in your code** all the time.

The reason is that I've never found a problem where type coercion is required for the solution, and when I need to convert one type into another, it's always better to do so explicitly:

```javascript
let price = "50";
let tax = 5;

let totalPrice = Number(price) + Number(tax);

console.log(totalPrice);
```

Using explicit type conversion functions such as `Number()` and `String()` will make your code clear and transparent. You don't need to guess the correct data type required in your program.

Type coercion is one of the unique features in JavaScript that may confuse beginners, so it's good to clear it up early.

Next, we'll learn about **JavaScript operators**.

