# 9 - Operators in JavaScript

As the name implies, operators are symbols you can use to perform operations on your data.

You've seen some examples of using the plus `+` operator to join multiple strings and add two numbers together. Of course, JavaScript has more than one operator as you'll discover in this section.

Since you've learned about data types and conversion previously, learning operators should be relatively easy.

## Arithmetic operators

The arithmetic operators are used to perform mathematical operations like additions and subtractions.

These operators are frequently used with number data types. Here's an example:

```javascript
console.log(10 - 3); // 7
console.log(2 + 4); // 6
```

In total, there are 8 arithmetic operators in JavaScript:

| Name           | Operation example | Meaning                                                  |
|--------------|-----------------|----------------------------------------------------------|
| Addition      | `x + y`          | Returns the sum between the two operands               |
| Subtraction   | `x - y`          | Returns the difference between the two operands        |
| Multiplication | `x * y`          | Returns the multiplication between the two operands    |
| Exponentiation | `x ** y`         | Returns the value of the left operand raised to the power of the right operand |
| Division      | `x / y`          | Returns the value of the left operand divided by the right operand |
| Remainder     | `x % y`          | Returns the remainder of the left operand after being divided by the right operand |
| Increment     | `x++`            | Returns the operand plus one                           |
| Decrement     | `x--`            | Returns the operand minus one                          |

These operators are pretty straightforward, so you can try them on your own.

As you've seen in the previous section, the `+` operator can also be used on string data to merge multiple strings as one:

```javascript
let message = "Hello " + "human!";
console.log(message); // Hello human!
```

When you add a number and a string, JavaScript will perform a type coercion and treat the number value as a string value:

```javascript
let sum = "Hi " + 89;
console.log(sum); // Hi 89
```

Using any other arithmetic operator with strings will cause JavaScript to return a `NaN` value.

## The assignment operator

The next operator to learn is the assignment operator, which is represented by the equals `=` sign.

In JavaScript, the assignment operator is used to assign data or a value to a variable.

You've seen some examples of using the assignment operator before, so here's a reminder:

```javascript
// Assign the string value 'Hello' to the 'message' variable
let message = "Hello";

// Assign the Boolean value true to the 'on' variable
let on = true;
```

You may have noticed that the equals sign has a slightly different meaning in programming than in math, and you're correct!

The assignment operator isn't used to compare if a number equals another number in programming.

If you want to do that kind of comparison, then you need to use the equal to `==` operator.

Assignment operators can also be combined with arithmetic operators, so that you can add or subtract values from the left operand.

See the table below for the types of assignment operators:

| Name                  | Operation example | Meaning              |
|----------------------|-----------------|----------------------|
| Assignment           | `x = y`          | `x = y`             |
| Addition assignment  | `x += y`         | `x = x + y`         |
| Subtraction assignment | `x -= y`       | `x = x - y`         |
| Multiplication assignment | `x *= y`   | `x = x * y`         |
| Division assignment  | `x /= y`         | `x = x / y`         |
| Remainder assignment | `x %= y`         | `x = x % y`         |

## The comparison operators

Comparison operators are used to compare two values. The operators in this category will return Boolean values: either `true` or `false`.

The following table shows all comparison operators available in JavaScript:

| Name             | Operation example | Meaning                                   |
|----------------|-----------------|-------------------------------------------|
| Equal          | `x == y`         | Returns `true` if the operands are equal |
| Not equal      | `x != y`         | Returns `true` if the operands are not equal |
| Strict equal   | `x === y`        | Returns `true` if the operands are equal and have the same type |
| Strict not equal | `x !== y`       | Returns `true` if the operands are not equal, or have different types |
| Greater than   | `x > y`          | Returns `true` if the left operand is greater than the right operand |
| Greater than or equal | `x >= y`   | Returns `true` if the left operand is greater than or equal to the right operand |
| Less than      | `x < y`          | Returns `true` if the left operand is less than the right operand |
| Less than or equal | `x <= y`      | Returns `true` if the left operand is less than or equal to the right operand |

Here are some examples:

```javascript
console.log(9 == 9); // true
console.log(9 != 20); // true
console.log(2 > 10); // false
console.log(2 < 10); // true
console.log(5 >= 10); // false
console.log(10 <= 10); // true
```

String comparisons are case-sensitive:

```javascript
console.log("ABC" == "ABC"); // true
console.log("ABC" == "abc"); // false
```

## Logical operators

Logical operators are used to check whether one or more expressions result in either `true` or `false`.

| Name          | Operation example | Meaning                                       |
|--------------|-----------------|-----------------------------------------------|
| Logical AND  | `x && y`         | Returns `true` if all operands are true      |
| Logical OR   | `x || y`         | Returns `true` if one of the operands is true |
| Logical NOT  | `!x`             | Reverse the result: returns `true` if false and vice versa |

Example:

```javascript
console.log(7 > 2 && 5 > 4); // true
```

## The `typeof` operator

JavaScript allows you to check the data type using the `typeof` operator:

```javascript
let x = 5;
console.log(typeof x); // 'number'
console.log(typeof "Nathan"); // 'string'
console.log(typeof true); // 'boolean'
```

### Exercise #3

Guess the result of these operators in action:

```javascript
console.log(19 % 3);
console.log(10 == 3);
console.log(10 !== "10");
console.log(2 < "10");
console.log("5" > 2);
console.log((false && true) || false);

