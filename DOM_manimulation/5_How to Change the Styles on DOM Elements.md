# How to Change the Styles on DOM Elements

There are two main ways of styling elements when working with the DOM in JavaScript. You can use the `.style` property or you can use classes. Each has its benefits and situations it's best suited for.

## Setting Styles With the `.style` Property

You use the `.style` property when you want to make specific changes to a single element. The `.style` property allows you to set styles directly as inline styles for elements. This means it overrides the styles you have in your CSS stylesheet.

Using the `.style` property, you get access to all the individual CSS properties. See the demo below:

```html
<h1>Styling elements with JavaScript</h1>
```

```javascript
const header = document.querySelector('h1');
console.log(header.style);
```

The `console.log` prints the CSS style declarations with all the CSS properties for that element.

Now, let's see an example of how to use the `.style` property.

```html
<h1>I love JavaScript</h1>
```

Here is an `h1` header. Now, let's add style to it using the `.style` property.

```javascript
const paragraph = document.querySelector('h1');

paragraph.style.color = 'white';
paragraph.style.backgroundColor = 'green';
```

**NOTE:** Because this is JavaScript, you cannot use the hyphen if the CSS property name includes two or more words. For example, in CSS you would write `background-color`. But in your JavaScript code, you need to use camel case. So `background-color` becomes `backgroundColor`.

You can also delete a style on an element by setting the value of the property to an empty string:

```javascript
element.style.propertyName = "";
```

---

## Setting Styles with Classes

With classes, you can create styles once and apply them to different elements. This helps make your code more maintainable.

### The `className` Property

The `className` property represents the `class` attribute of a DOM element. You can use it to get or set the value of the class attribute.

Here's an example:

```html
<p class="food rice-dish">Jollof rice</p>
```

```javascript
const jollofParagraph = document.querySelector('p');

console.log(jollofParagraph.className);

jollofParagraph.className = 'favorite';

console.log(jollofParagraph.className);
```

The `className` also reads or replaces the current class. In the example above, the first log statement prints the original value of the class. After updating `className`, the second log statement prints the new value for class.

But there is a more flexible property. What if instead of replacing the old class with a new class, you wanted to add another class? That's where the `classList` property comes in.

### The `classList` Property

With the `classList` property, you can add and remove classes. You can also toggle classes, replace existing class values with new ones, and even check if the class contains a specific value.

Here's an example:

```html
<p class="food">Jollof rice</p>
```

```javascript
const jollofParagraph = document.querySelector('p');
console.log(jollofParagraph.classList);
```

#### Adding Classes with `classList.add()`

```javascript
jollofParagraph.classList.add('fav', 'tasty');

console.log(jollofParagraph.classList);
```

The code adds two new classes `fav` and `tasty` to the class list.

#### Removing Classes With `classList.remove()`

```javascript
jollofParagraph.classList.remove('tasty');

console.log(jollofParagraph.classList);
```

The code removes the class `tasty` from the class list.

#### Replacing Classes with `classList.replace()`

```javascript
jollofParagraph.classList.replace('fav', 'favorite');

console.log(jollofParagraph.classList);
```

The code replaces the class `fav` with `favorite`.

#### Check the Presence of a Class with `classList.contains()`

```javascript
const isFavorite = jollofParagraph.classList.contains('favorite');
const isSoup = jollofParagraph.classList.contains('soup');

console.log("Contains favorite: ", isFavorite);
console.log("Contains soup: ", isSoup);
```

The code checks if the class passed to it is contained in the class list.

It returns `true` if it is included in the class list (for example `favorite`) and `false` if it is not included in the class list (for example `soup`).

#### Toggling a Class with the `classList.toggle()`

When you use the `toggle` property, it first checks if the class exists. If it exists, it will remove it. And if it doesn't exist, it will add it.

```javascript
jollofParagraph.classList.toggle('favorite');
console.log(jollofParagraph.classList);

jollofParagraph.classList.toggle('favorite');
console.log(jollofParagraph.classList);

jollofParagraph.classList.toggle('favorite');
console.log(jollofParagraph.classList);
```

The first time the toggle runs, `favorite` exists in the class list, so the toggle removes it.

The second time the toggle runs, `favorite` doesn't exist, so the toggle adds `favorite` to the class list.

The next time the toggle runs, `favorite` now exists again, so it removes it from the class list.

The toggle keeps adding or removing the value from the class list depending on whether it's present or absent.

