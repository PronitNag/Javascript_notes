## 3 - Quick Console Introduction

The console is a text-based interface that you can use to type and run commands on your computer. On Windows, it's called the **Command Line**. On macOS and Linux, it's known as the **Terminal**.

You're not going to use all the commands available within the console. In fact, you only need to know **7 basic commands** to help you run JavaScript code.

First, open the console program on your computer and type the `pwd` command:

```sh
pwd
```

This is the command you use to find out which directory your terminal is currently on. `pwd` is short for **print working directory**.

To change the working directory, you need to run the `cd` command.

Here's an example to move into a child directory:

```sh
cd directory_name/directory_name
```

To move up to a parent directory, you specify `..` next to the command:

```sh
cd ..
```

To go up more than one directory, use `../..`

To clear your console from previous commands and output, use the `clear` command:

```sh
clear
```

To print out the list of files and directories in the current directory, run the `ls` command:

```sh
ls
```

To create a new file, use the `touch` command followed by the file name and extension:

```sh
touch index.js
```

The command above will create a new JavaScript file named `index.js` in the current working directory.

To create a new directory, use the `mkdir` command followed by the directory name:

```sh
mkdir my_project
```

To run JavaScript using Node.js, specify `node` followed by the file name as follows:

```sh
node index.js
```

You'll see any output from the code in the same console.

There are lots of things you can do with the console, but these **7 commands** would be enough because we only need it to run JavaScript code.

Next, let's run your first JavaScript program!


