## 14 - Objects in JavaScript

An object is a special data type that allows you to store more than one value, just like an array.

The difference between an object and an array is that an array stores data as a list of items, while an object stores data in a key:value pair format.

### Example: Array vs. Object

Suppose you want to store information about a book in your program.

#### Using Variables:
```javascript
let bookTitle = "JavaScript Introduction";
let bookAuthor = "Nathan Sebhastian";
```
While it works fine, it certainly isn't the best way to store related values.

#### Using an Array:
```javascript
let myBook = ["JavaScript Introduction", "Nathan Sebhastian"];
```
This groups related data together, but you have no way to add context to the values.

#### Using an Object:
```javascript
let myBook = {
  title: "JavaScript Introduction",
  author: "Nathan Sebhastian",
};
```
An object is declared using curly brackets `{}` and stores data in a key:value format.

### Object Properties

An object item is known as a property, with the key as the property name and the value as the property value.

#### Adding a Function as a Property:
```javascript
let myBook = {
  title: "JavaScript Introduction",
  author: "Nathan Sebhastian",
  describe: function () {
    console.log(`Book title: ${this.title}`);
    console.log(`Book author: ${this.author}`);
  },
};
```
Here, the `describe` key is a function that prints the title and author. The `this` keyword refers to the `myBook` object.

### Accessing Object Properties

#### Using Dot Notation:
```javascript
console.log(myBook.title);
console.log(myBook.author);
```

#### Using Square Brackets:
```javascript
console.log(myBook["title"]);
console.log(myBook["author"]);
```
Ensure you wrap the property name in quotes when using square brackets.

### Adding a New Property

```javascript
myBook.year = 2023;
myBook["publisher"] = "CodeWithNathan";
console.log(myBook);
```
#### Output:
```javascript
{
  title: 'JavaScript Introduction',
  author: 'Nathan Sebhastian',
  year: 2023,
  publisher: 'CodeWithNathan'
}
```

### Modifying Object Properties

```javascript
myBook.author = "John Doe";
console.log(myBook);
```
#### Output:
```javascript
{
  title: 'JavaScript Introduction',
  author: 'John Doe'
}
```

### Deleting Object Properties

```javascript
delete myBook.author;
console.log(myBook);
```
#### Output:
```javascript
{ title: 'JavaScript Introduction' }
```

### Checking if a Property Exists

```javascript
let person = {
  firstName: "Nathan",
  lastName: "Sebhastian"
};

console.log('firstName' in person); // true
console.log('age' in person); // false
```

## Exercise #8
Create a `person` object with the following properties:
- `name` - the person's name
- `age` - the person's age
- `greet()` - a function to introduce the person

#### Example Output:
```javascript
person.greet();
// Output: Hello! My name is Alex and I'm 22 years old.
```

## Final Exercise: Build a Cash Register Machine

The cash register should be able to:
1. **Add items** to a shopping cart.
2. **Calculate total price** of all items.
3. **Apply discounts** (10% if total > 400).
4. **Process payment** and determine if the customer has enough money.

### Available Items:
- Phone: $300
- Smart TV: $220
- Gaming Console: $150

### Key Methods:
1. `addItem(itemName)`: Adds an item to the shopping cart if available.
2. `calculateTotalPrice()`: Calculates the total cost.
3. `pay(amount)`: Processes payment, applies discounts, and gives change if applicable.

### Implementation Steps:
- Use objects, arrays, conditionals, and loops to build the program.
- Print appropriate messages using `console.log()`.
- Handle edge cases where payment is greater than, equal to, or less than the total price.

Give it a try first before checking the solution. Good luck!

