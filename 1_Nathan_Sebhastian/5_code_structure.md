# 5 - JavaScript Code Structure

A computer program is a series of pieces of code written in a text file. These text files are then run through a software that's designed specially for running the code. The Node.js software you downloaded previously is the tool that processes JavaScript code.

Before we go further, let's understand the structure of code.

## Statements

A statement is a single instruction for the computer to run. Think of it like a sentence, but for computers. We can end a statement by using a semicolon `;` just like we can end a sentence using a dot `.`

You can write multiple statements in a single line, but the convention is to write one statement per line:

```javascript
// This is hard to read
console.log("Hello World!"); console.log("I'm learning JavaScript");

// Now it's better
console.log("Hello World!");
console.log("I'm learning JavaScript");
```

Each statement is an expression of some action that needs to be carried out by the software that executes the code.

## Comments

In programming, comments are text we use to communicate the context of the code written in the file.

To write a comment in JavaScript, you need to add two forward slashes `//` before the comment as shown below:

```javascript
// This is a comment
// This is also a comment

// Below print two lines of statements
console.log("Hello World!");
console.log("I'm learning JavaScript");
```

Comments are ignored by the language processor, so you can use comments to disable some code without having to delete that code.

The code below shows how to disable the second print statement:

```javascript
console.log("Hello World!");
// console.log("I'm learning JavaScript");
```

## Execution Flow

A language processor such as Node.js executes statements in a top-down approach. The statement written in the first line will be executed before the second line, then continue down to the last line:

```javascript
console.log("Hello World!");
console.log("I'm learning JavaScript");

// Printing numbers
console.log(1);
console.log(2);
console.log(3);
```

### Output:

```
Hello World!
I'm learning JavaScript
1
2
3
```

If you want to print the numbers before the text, then you need to move the corresponding `console.log()` lines to the top.

## Exercise #1

Try to print your name, age, and occupation on the console.

The output would look as follows:

```
John Doe
19
Student
```

Now that you understand the basic code structure of JavaScript, let's continue with learning variables next.

