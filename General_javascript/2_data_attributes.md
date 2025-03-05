# Data Attributes in JavaScript

## Introduction

One of the best ways to store data in HTML is with data attributes. These data attributes can be used to do some pretty cool things in CSS without the need for JavaScript, but data attributes are most useful when combined with JavaScript. In this article, I will teach you exactly how to use data attributes in JavaScript and what makes them so powerful.

## Data Attribute Introduction

To get started talking about data attributes, we need to first have some HTML with data attributes. To create a data attribute in HTML, we just need to add a custom attribute to our HTML element that starts with `data-`.

```html
<div
  id="test-div"
  data-first-name="Kyle"
  data-last-name="Cook"
  data-active
></div>
```

## Reading Data Attributes

We now have a `div` with three custom data attributes. Now let’s move over to JavaScript to see how we would access these data attributes.

```js
const div = document.getElementById("test-div");

console.log(div.dataset);
```

The `dataset` property on an element will return a `DOMStringMap`, which is essentially just an object that contains all the custom data attributes of an element. Our dataset looks like this:

```js
{
  active: "",
  firstName: "Kyle",
  lastName: "Cook"
}
```

### Observations

1. All properties are converted from kebab-case (`first-name`) to camelCase (`firstName`). This is because in JavaScript, object properties are primarily written in camelCase, making them easier to work with.
2. The `active` property has a value of `""`. Any data attribute without a value is assumed to have an empty string as its value.

To access an individual data attribute, we treat it like a property on an object:

```js
console.log(div.dataset.firstName); // Kyle
console.log(div.dataset.lastName); // Cook
```

## Writing Data Attributes

To create a new data attribute in JavaScript, we add a new property to the `dataset` object:

```js
const div = document.getElementById("test-div");

div.dataset.test = "Hi";
console.log(div.dataset.test); // Hi
```

This updates both the dataset object and the HTML, resulting in:

```html
<div
  id="test-div"
  data-test="Hi"
  data-first-name="Kyle"
  data-last-name="Cook"
  data-active
></div>
```

## Updating Data Attributes

Updating a data attribute is simple, just like modifying an object property:

```js
const div = document.getElementById("test-div");

div.dataset.firstName = "Sally";
console.log(div.dataset.firstName); // Sally
```

This modifies the HTML as well:

```html
<div
  id="test-div"
  data-first-name="Sally"
  data-last-name="Cook"
  data-active
></div>
```

## Deleting Data Attributes

To delete a data attribute, we use the `delete` keyword:

```js
const div = document.getElementById("test-div");

delete div.dataset.active;
console.log(div.dataset.active); // undefined
```

This updates the HTML:

```html
<div id="test-div" data-first-name="Sally" data-last-name="Cook"></div>
```

## Real-World Example

Consider the following HTML:

```html
<button>Open Modal 1</button>
<button>Open Modal 2</button>

<div id="modal-1">Modal 1</div>
<div id="modal-2">Modal 2</div>
```

We want each button to open its corresponding modal. Instead of writing separate event listeners for each button, we use data attributes:

```html
<button data-modal-id="modal-1">Open Modal 1</button>
<button data-modal-id="modal-2">Open Modal 2</button>

<div id="modal-1">Modal 1</div>
<div id="modal-2">Modal 2</div>
```

Now, we can write reusable JavaScript:

```js
const buttons = document.querySelectorAll("[data-modal-id]");

buttons.forEach(button => {
  button.addEventListener("click", () => {
    const modalId = button.dataset.modalId;
    const modal = document.getElementById(modalId);
    modal.classList.add("show");
  });
});
```

### Explanation

- We select all elements with `data-modal-id`.
- We loop through them and add a click event listener.
- When clicked, we retrieve the modal ID from `dataset` and add the `show` class to the corresponding modal.

This approach is scalable. If we add a new button for another modal, the existing JavaScript will handle it without modification.

## Conclusion

Data attributes in JavaScript are incredibly useful. They allow you to write flexible code, reducing the need for custom event listeners for each new element. By leveraging data attributes, you can focus on structuring your HTML while keeping your JavaScript maintainable and scalable.
