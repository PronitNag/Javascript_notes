# 6 - JavaScript Variables

Before explaining what a variable is, I want you to change the code you've written in the `index.js` file.

Change the code in that file as follows:

```javascript
let message = "Hello World!";
console.log(message);
```

Next, run the code using the `node index.js` command. You'll see the same output as when you write the `'Hello World!'` message directly inside the `console.log()` function. How can this be?

This is because the message written in the code above is a variable.

In programming, a variable is simply a name that you give to a value so that you can access that value later. You can think of a variable as a label that can be tagged to a certain value, so you can refer to the value using the label.

To declare a variable, you need to type the keyword `let` followed by the variable name.

The first line in the code tells JavaScript to associate the `message` variable with the value `Hello World!`:

```javascript
let message = "Hello World!";
```

In the second line, JavaScript is instructed to print the value of `message`, and that's exactly what it does.

You can change the value of your variable by re-assigning another value as follows:

```javascript
message = "Hello World!";
console.log(message);
message = "Nice weather!";
console.log(message);
```

Run the file and you'll see two lines printed as the output:

```
Hello World!
Nice weather!
```

Variables are used to reference data so that you can use the same data multiple times in your program.

## Variable Naming

JavaScript has a few naming rules that you need to know to avoid naming errors.

- Variable names can only contain alphabet letters, numbers, and underscores (`_`). This means you can name your variable `message`, `message_1`, `message_2`.
- The first character of the variable name must not be a number. `message_1` is okay. `1_message` is not.
- You can't use reserved keywords such as `console` because they are used by JavaScript to do certain things. There are many other keywords used by JavaScript that you'll learn in the following sections such as `if`, `for`, and `while`.
- Variable names are case-sensitive, which means `Message`, `MESSAGE`, and `message` can be used to create three different variables. But of course, I don't recommend using similar names as it causes confusion.

Sometimes, you need more than one word to declare a variable name. JavaScript has two naming conventions that are used worldwide:

### camelCase
Camel case is a naming convention that uses an uppercase letter for the first character for subsequent words. Here's an example:

```javascript
let myAwesomeVariable;
```

### snake_case
The snake case naming convention uses an underscore to separate words. Here's an example:

```javascript
let my_awesome_variable;
```

Both are acceptable naming conventions, but you should stick to one of them in your code to avoid confusion.

## Constant Variable

There are times when you need to store a value that never changes in a variable.

A **constant variable** is a variable that doesn't change its value as long as the program is running. In other programming languages, changing the value of a constant will produce an error.

In JavaScript, a constant variable is declared using the `const` keyword.

The following shows how to declare two constants in JavaScript:

```javascript
const FILE_SIZE_LIMIT = 2000;
const MAX_SPEED = 300;
```

The naming convention for a constant is to use all uppercase letters, although using lowercase letters also works. The uppercase is just a standard to make constants stand out more.

## The `var` Keyword

The `var` keyword is used to declare variables with a global scope. This keyword was the only keyword you could use to declare variables before JavaScript released the new `let` and `const` keyword in 2015.

As of today, you should avoid using `var` if you can, since `var` can introduce bugs that you can avoid by using the `let` keyword.

To show you what I mean, consider the following example:

```javascript
if(true) {
    var name = "Nathan";
}

console.log(name);
```

The code above will print the `name` variable just fine, but it really should not because the variable `name` is declared inside the `if` block.

This is because any variable declared using the `var` keyword is accessible from everywhere. The scope of that variable is global.

On the other hand, the `let` keyword has a **block scope**, which means the variable is only accessible from the block and all its child blocks.

But why bother with scoping the variable? This is because when you have hundreds or thousands of code lines, it can become frustrating to trace an error that occurs because of global variables.

There's a principle in software development called **"principle of least exposure"**, which means you don't expose any part of your program that's unnecessary.

Block scoping a variable ensures that a variable is exposed and accessible only in parts of your codebase that require the variable.

A variable declared using the `let` keyword is identical to a variable declared using `var` except for the scope level.

```javascript
if(true) {
    let name = "Nathan";
}

console.log(name);  // Error: name is not defined
```

This also means that you now have `var`, `let`, and `const` keywords to declare a variable. Which one to use?

- In general, you can declare a variable with `const` first. When you code your application and realize that you need to change the variable assignment, you can change the declaration to `let`.
- If you know from the start that the variable's value will change, then you can use `let` immediately.
- Just don't use `var` today or people might get mad at you.

## Exercise #2

Write a program with three variables, each with the following value:

- The first variable contains your name
- The second variable contains your age
- The third variable contains your occupation

Then print the variables using the `console.log()` method. Here's the example output:

```
John Doe
Student
19
```

## Summary

How you use variables to make a program that does what you want it to do is one of the most important skills you can have as a programmer.

But before you learn more about how to make use of variables, let's learn about data types in JavaScript.

