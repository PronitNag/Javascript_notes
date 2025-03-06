## 10 - JavaScript Arrays

An array is an object data type that can be used to hold more than one value. An array can be a list of strings, numbers, booleans, objects, or a mix of them all.

To create an array, you need to use the square brackets `[]` and separate the items using a comma.

Here's how to create a list of strings:

```javascript
let birds = ['Owl', 'Eagle', 'Parrot', 'Falcon'];
```

You can think of an array as a list of items, each stored in a locker compartment:

*Array as a locker illustration*

You can also declare an empty array without any value:

```javascript
let birds = [];
```

An array can also have a mix of values like this:

```javascript
let mixedArray = ['Bird', true, 10, 5.17];
```

The array above contains a string, a boolean, an integer, and a float.

### Array Index Position

JavaScript remembers the position of the elements within an array. The position of an element is also called an index number.

Going back to the locker example, you can think of index numbers as the locker numbers. The index number starts from `0` as follows:

*Array index numbers as locker numbers*

To access or change the value of an array, you need to add the square brackets notation `[x]` next to the array name, where `x` is the index number of that element. Here's an example:

```javascript
// Access the first element in the array
myArray[0];

// Access the second element in the array
myArray[1];
```

Suppose you want to print the string `'Owl'` from the `birds` array. Here's how you can do it:

```javascript
let birds = ['Owl', 'Eagle', 'Parrot', 'Falcon'];

console.log(birds[0]); // Owl
console.log(birds[1]); // Eagle
```

You need to type the name of the array, followed by the index number wrapped in square brackets.

You can also assign a new value to a specific index using the assignment operator.

Let's replace `'Parrot'` with `'Vulture'`:

```javascript
let birds = ['Owl', 'Eagle', 'Parrot', 'Falcon'];
birds[2] = 'Vulture';

console.log(birds);
// ['Owl', 'Eagle', 'Vulture', 'Falcon']
```

Because the array index starts from zero, the value `'Parrot'` is stored at index `2` and not `3`.

### Special Methods for Array Manipulation

Since an array is an object, you can call methods that are provided by JavaScript to manipulate the array values.

For example, you can use the `push()` method to add an item to the end of the array:

```javascript
let birds = ['Owl', 'Eagle'];

birds.push('Sparrow');

console.log(birds);
// ['Owl', 'Eagle', 'Sparrow']
```

Another method called `pop()` can be used to remove an item from the end of an array:

```javascript
let birds = ['Owl', 'Eagle', 'Sparrow'];

birds.pop();

console.log(birds);
// ['Owl', 'Eagle']
```

The `unshift()` method can be used to add an item from the front at index `0`:

```javascript
let fishes = ['Salmon', 'Goldfish', 'Tuna'];

fishes.unshift('Sardine');

console.log(fishes);
// ['Sardine', 'Salmon', 'Goldfish', 'Tuna']
```

On the other hand, the `shift()` method can be used to remove an item from index `0`:

```javascript
let fishes = ['Salmon', 'Goldfish', 'Tuna'];

fishes.shift();

console.log(fishes);
// ['Goldfish', 'Tuna']
```

The `indexOf()` method can be used to find and return the index of an item in the array.

The method will return `-1` when the item isn't found inside the array:

```javascript
let fishes = ['Salmon', 'Goldfish', 'Tuna'];

let pos = fishes.indexOf('Tuna');

console.log(pos); // 2
```

To get the size of an array, you can access the `length` property:

```javascript
let fishes = ['Salmon', 'Goldfish', 'Tuna'];

console.log(fishes.length); // 3
```

Note that we don't add parentheses next to the `length` keyword above. This is because `length` is a property of the array object and not a method.

We'll learn more about objects in the coming tutorials.

### Exercise #4

Create an array named `colors` that includes the `'red'`, `'green'`, and `'blue'` colors.

1. First, add a `'black'` color after the last index of the array. Then print the array.
2. Next, remove the value `'red'` and swap the position of `'green'` and `'blue'`. Print the array.
3. Finally, add the color `'yellow'` on the first index of the array, then print the array.

The result output is as follows:

```javascript
[ 'red', 'green', 'blue', 'black' ]
[ 'blue', 'green', 'black' ]
[ 'yellow', 'blue', 'green', 'black' ]
```

You need to modify the original array using the methods explained in this section.

