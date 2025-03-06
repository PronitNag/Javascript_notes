# 12 - Control Flows (Loops) in JavaScript

As you program an application in JavaScript, you'll often need to write a piece of code that needs to be executed repeatedly.

Let's say you want to write a program that prints the numbers 1 to 10 in the console. You can do it by calling `console.log` 10 times like this:

```javascript
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);

// and so on..
```

This works, but there's a better way to write this kind of repetitive task.

A **Loop statement** is another category of control flow statement used to execute a block of code multiple times until a certain condition is met.

There are two loop statements used in JavaScript:

1. **The for statement**
2. **The while statement**

Let's learn how to use these statements in practice.

## The for statement

Instead of repeating yourself 10 times to print the numbers 1 to 10, you can use the `for` statement and write just a single line of code as follows:

```javascript
for (let x = 1; x <= 10; x++) {
  console.log(x);
}
```

The `for` statement is followed by parentheses `()` which contain 3 expressions:

1. **Initialization expression:** Declares a variable to be used as the source of the loop condition. Represented as `x = 1` in the example.
2. **Condition expression:** Evaluates the variable in initialization for a specific condition. Represented as `x <= 10` in the example.
3. **Arithmetic expression:** Increments or decrements the variable value at the end of each loop.

These expressions are separated by a semicolon (`;`).

### Syntax

```javascript
for ([initialization]; [condition]; [arithmetic expression]) {
  // As long as condition returns true,
  // This block will be executed repeatedly
}
```

### Examples

**Decrementing loop:**

```javascript
for (let x = 10; x >= 1; x--) {
  console.log(x);
}
```

**Using shorthand arithmetic operators (`+=` and `-=`):**

```javascript
for (let x = 1; x < 20; x += 3) {
  console.log(x);
}
```

Once the loop is over, JavaScript will continue executing any code below:

```javascript
for (let x = 1; x < 2; x++) {
  console.log(x);
}
console.log("The for loop has ended");
console.log("Continue code execution");
```

### When to use a for loop

The `for` loop is useful when you **know** how many times you need to execute a repetitive task.

Example: Simulating a coin toss 10 times:

```javascript
let heads = 0;
let tails = 0;
for (let x = 1; x <= 10; x++) {
  if (Math.random() < 0.5) {
    tails++;
  } else {
    heads++;
  }
}

console.log("Tossed the coin ten times");
console.log(`Number of heads: ${heads}`);
console.log(`Number of tails: ${tails}`);
```

## The while statement

The `while` loop is used to run a block of code **as long as** the condition evaluates to `true`.

### Syntax

```javascript
while (condition) {
  statement;
}
```

### Example

```javascript
let i = 0;

while (i < 6) {
  console.log(`The value of i = ${i}`);
  i++;
}
```

**Warning:** Ensure the condition eventually turns `false` to avoid infinite loops. The following code causes an infinite loop:

```javascript
let i = 0;

while (i < 6) {
  console.log(`The value of i = ${i}`);
}
```

### When to use a while loop

Use a `while` loop when you **don't know** how many times you need to execute the code.

Example: Find out how many times you need to flip a coin until it lands on heads:

```javascript
let flips = 0;
let isHeads = false;

while (!isHeads) {
  flips++;
  isHeads = Math.random() < 0.5;
}

console.log(`It took ${flips} flips to land on heads.`);
```

## Exercise #6

Write a program that prints a half pyramid using asterisks `*` as shown below:

```
*
**
***
****
*****
```

Next, print a reverse half pyramid:

```
*****
****
***
**
*

