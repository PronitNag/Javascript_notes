# How to Work with Attributes of DOM Elements

HTML attributes provide useful information about HTML elements. These attributes are always included in the opening tag of the element. An attribute is made up of a name and a value (though there are exceptions where only a name is present).

As the browser generates the DOM based on the HTML structure, it translates these attributes into dynamic properties of the DOM objects.

## Example

Assume there's a button in the HTML document with the following attributes:

```html
<button id="myBtn" type="submit">Click Here</button>
```

For this example, the browser will create an `HTMLButtonElement` object in the DOM. And the object will have properties matching the attributes:

- `HTMLButtonElement.id` with a value of `myBtn`.
- `HTMLButtonElement.type` with a value of `submit`.

To interact with and manipulate these attributes using JavaScript, you can use methods like `getAttribute` and `setAttribute` to directly access the properties.

## The `getAttribute` Method

Like the name suggests, you can use this method to get the value of an existing attribute on an element.

It accepts an argument (the name of the attribute) and returns the value of the attribute. If the attribute you passed to it as an argument does not exist on the element, the method will return `null`.

### Example

```html
<img src="image.jpg" alt="An example image">
```

```javascript
const imageElement = document.querySelector('img');
console.log(imageElement.getAttribute('src'));
```

Using the `getAttribute` method in the above example, you can get the value of the `src` attribute for the image element.

## The `setAttribute` Method

This is used to set or change the attribute of an element. The method takes in two arguments:
1. The name of the attribute you want to change.
2. The new value you want to give the attribute.

### Example

```html
<img src="image.jpg" alt="An example image">
```

```javascript
const imageElement = document.querySelector('img');

console.log("BEFORE:", imageElement.getAttribute('src'));
imageElement.setAttribute('src', 'new-image.jpg');
console.log("AFTER:", imageElement.getAttribute('src'));
```

The `setAttribute` method is used to update the value of the `src` attribute.

When you pass an argument to the `setAttribute` method and that attribute doesn't exist on the element, it will create a new attribute. For example, you can add a `height` property to the image element like so:

```javascript
const imageElement = document.querySelector('img');

console.log("BEFORE:", imageElement.getAttribute('height'));
imageElement.setAttribute('height', '200');
console.log("AFTER:", imageElement.getAttribute('height'));
```

The first log statement returns `null` because the `height` attribute was non-existent. But after setting it with the `setAttribute` method, the second log statement returns the correct value of the `height`.

## The `removeAttribute` Method

In the previous section, you learned how to add a new attribute using the `setAttribute` method. What if you wanted to remove an existing attribute?

You can use the `removeAttribute` method. You pass in the name of the attribute you want to remove from the element as an argument to the method.

### Example

```html
<img src="image.jpg" alt="An example image" height="200">
```

```javascript
const imageElement = document.querySelector('img');

console.log("BEFORE:", imageElement.getAttribute('height'));
imageElement.removeAttribute('height');
console.log("AFTER:", imageElement.getAttribute('height'));
```

Before using `removeAttribute`, the first log statement prints the value of the `height` attribute, `200`. But after using the `removeAttribute` method, the second log statement prints `null`, confirming the removal of the `height` attribute from the image element.

## The `hasAttribute` Method

Another method for working with attributes in the DOM is the `hasAttribute` method. You can use this method to check whether or not an element has a specific attribute.

The `hasAttribute` method returns `true` if the specified attribute exists and returns `false` if it doesn't.

### Example

```html
<img src="image.jpg" alt="An example image" height="200">
```

```javascript
const imageElement = document.querySelector('img');

console.log("HEIGHT", imageElement.hasAttribute('height'));
console.log("WIDTH", imageElement.hasAttribute('width'));
```

The check for `height` returns `true` because it's an existing attribute while the check for `width` returns `false` because it doesn't exist.

