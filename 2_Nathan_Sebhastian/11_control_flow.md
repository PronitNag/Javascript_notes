## 11 - Control Flows (Conditionals) in JavaScript

Up until now, the JavaScript code you've written is executed line by line from top to bottom. But what if you want to run some lines of code only when a certain condition is met?

A computer program usually needs to take into account many different conditions that can arise during the program's execution.

This is similar to how a human makes decisions in their life. For example, do you have money to cover the vacation to Japan? If yes, go. If not, then save more money!

This is where control flow comes in. Control flow is a feature in a programming language that allows you to selectively run specific code based on the different conditions that may arise.

Using control flows allows you to define multiple paths a program can take based on the conditions present in your program.

There are two types of control flows commonly used in JavaScript: **conditionals** and **loops**.

This section will focus on the conditional statements such as:

- `if...else` statement
- `switch...case` statement

You'll learn about loop statements in the next section.

---

### The `if...else` statement

The `if` statement allows you to create a program that runs only if a specific condition is met.

#### Syntax

```javascript
if (condition) {
  // code to execute if condition is true
}
```

#### Example

Suppose you want to go on a vacation that requires 5000 dollars.

```javascript
let balance = 7000;

if (balance > 5000) {
  console.log("You have the money for this trip. Let's go!");
}
```

Change the value of `balance` to `3000`, and you'll get no response because the code inside the `if` statement is only executed when the condition is true.

```javascript
let balance = 7000;

if (balance > 5000) {
  console.log("You have the money for this trip. Let's go!");
}
console.log("The end!");
```

#### Using `else`

```javascript
let balance = 7000;

if (balance > 5000) {
  console.log("You have the money for this trip. Let's go!");
} else {
  console.log("Sorry, not enough money. Save more!");
}
console.log("The end!");
```

#### Using `else if`

```javascript
let balance = 7000;

if (balance > 5000) {
  console.log("You have the money for this trip. Let's go!");
} else if (balance > 3000) {
  console.log("You only have enough money for a staycation");
} else {
  console.log("Sorry, not enough money. Save more!");
}
console.log("The end!");
```

---

### The `switch...case` statement

The `switch` statement allows you to control the execution flow of your code in a structured way.

#### Example

```javascript
let age = 15;
switch (age) {
  case 10:
    console.log("Age is 10");
    break;
  case 20:
    console.log("Age is 20");
    break;
  default:
    console.log("Age is neither 10 or 20");
}
```

#### Important Notes:
- `switch` statements do **not** perform type coercion.
- The `break` statement is necessary to prevent the execution of subsequent cases.
- The `default` case is executed if no matching case is found.

```javascript
switch (0) {
  case 1:
    console.log("Value is one");
  case 0:
    console.log("Value is zero");
  default:
    console.log("No matching case");
}
```

This will output:

```
Value is zero
No matching case
```

---

### Switch vs If-Else

Use `switch` when dealing with multiple discrete values, like days of the week:

#### Using `if-else`

```javascript
let weekdayNumber = 1;

if (weekdayNumber === 0) {
  console.log("Sunday");
} else if (weekdayNumber === 1) {
  console.log("Monday");
} else if (weekdayNumber === 2) {
  console.log("Tuesday");
} else {
  console.log("Invalid weekday number");
}
```

#### Using `switch`

```javascript
let weekdayNumber = 1;

switch (weekdayNumber) {
  case 0:
    console.log("Sunday");
    break;
  case 1:
    console.log("Monday");
    break;
  case 2:
    console.log("Tuesday");
    break;
  default:
    console.log("Invalid weekday number");
}
```

---

### Exercise #5

A primary school is giving different rewards based on the student's grade:

- Students that got an **A** will get a **Chocolate**
- Students that got a **B** will get a **Cookie**
- Students that got a **C** will get a **Candy**
- For any other value, print `"No reward to give."`

Create a variable named `grade` that will store the student's grade.

#### Example Output:

```
You got an A, so here's a Chocolate for you!
You got a B, here's a Cookie for you!
You got a C, there's room for improvement and here's your Candy!
```

Use either `if...else` or `switch...case` to implement the logic.

