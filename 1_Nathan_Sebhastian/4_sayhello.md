# 4 - Time to Say Hello World!

It's time to run your first JavaScript program using Node.

## Creating a New JavaScript File

From the console, create a new JavaScript file named `index.js` using the `touch` command:

```sh
touch index.js
```

Next, open the file using VSCode and write the following line of code into the file:

```js
console.log("Hello World!");
```

## Running the Script

Back on the console, run this script with Node:

```sh
node index.js
```

The console should execute the `index.js` file and print:

```
Hello World!
```

You've just run your very first JavaScript program using Node.js. Excellent!

## How the Code Works

When you run the `node index.js` command, the Node.js program starts reading the script line by line from top to bottom.

The Node program sees that you wrote the word `console.log` followed by parentheses `()`, so it knows that you're instructing it to print something. The program then reads what you put in the parentheses and prints it out on the console.

In your VSCode or other text editor, you should see different parts of your code highlighted with different colors. This is a feature of the text editor called **syntax highlighting**, and it's really useful to help you distinguish different parts of the code.

- The `log` keyword is a function, so it gets highlighted in one color.
- The words in the parentheses have another color.

## Understanding Functions and Objects

A **function** is simply a piece of code that's used to perform a certain task. The `log()` function is used to "print" whatever you put inside the parentheses.

On the other hand, the `console` keyword is an **object**, which is a standalone property that gives access to certain functionalities.

We'll learn more about functions and objects later. For now, just remember that the `console.log()` keyword is used to print things to the console.

---

### Next: Learning JavaScript Code Structure

