# Data Attributes in JavaScript

## Introduction

- One of the best ways to store data in HTML is with data attributes.
-These data attributes can be used to do some pretty cool things in CSS without the need for JavaScript, but data attributes are most useful when combined with JavaScript. 

## Data Attribute Introduction


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

