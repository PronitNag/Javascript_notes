# What is the difference between `innerText`, `textContent`, and `innerHTML`?

Let's learn about `innerText`, `textContent`, and `innerHTML`.

These are properties that you can access in JavaScript to get or change the content of an HTML element. Even if they may look very similar at first, they do have key differences. Choosing the right one depends on your specific use case, so let's dive in.

## Let's start with `innerText`

`innerText` represents the visible text content of the HTML element and its descendants. This property doesn't include **hidden text** or HTML tags, only rendered text.

For example, here you can see a `div` element that contains two paragraphs:

```html
<div id="container">
  <p>Hello, World!</p>
  <p>I'm learning JavaScript</p>
</div>
```

If we get a reference to this HTML element in our JavaScript code using `getElementById()`, we can access the `innerText` property of this element:

```javascript
const container = document.getElementById("container");
console.log(container.innerText);
```

This is the inner text of this element:

```
Hello, World!
I'm learning JavaScript
```

The property returns a string with the text contained within the element, **including text from its descendants**.

You should know that `innerText` only returns the text that is visible at the particular moment when the string is requested. If a **child element is hidden**, its text won't be visible.

This is an example where the second paragraph is hidden:

```html
<div id="container">
  <p>Hello, World!</p>
  <p hidden>I'm learning JavaScript</p>
</div>
```

If we try to log the `innerText` again, now the output won’t have the text of the second paragraph:

```javascript
console.log(container.innerText);
```

This will be the output:

```
Hello, World!
```

You can set the `innerText` of an HTML element like this, but this will replace the existing text and **add a line break (`br`) element** for every line break:

```javascript
container.innerText = "JavaScript is awesome!";
```

Since `innerText` takes visibility into account, getting its value triggers a process called **"reflow"**, that recalculates the position of certain elements on the website. This process can be computationally intensive, so you should avoid triggering it if possible.

---

## Great. Now let's talk about `textContent`

`textContent` returns the **plain text content** of an element, including all the text within its descendants.

The most important difference between `innerText` and `textContent` is that `textContent` always returns the full text content of an HTML element and its descendants, regardless of whether it's visible or hidden.

Here we have the same example in HTML:

```html
<div id="container">
  <p>Hello, World!</p>
  <p>I'm learning JavaScript</p>
</div>
```

If you try to access this property, you'll see the text of the element and its descendants as the output, keeping the indentation and spacing:

```javascript
const container = document.getElementById("container");
console.log(container.textContent);
```

```
Hello, World!
I'm learning JavaScript
```

If an HTML element is not visible, like you can see over here, where we’ve hidden the second paragraph, its text will still be included in this property:

```html
<div id="container">
  <p>Hello, World!</p>
  <p hidden>I'm learning JavaScript</p>
</div>
```

You will see the same output:

```
Hello, World!
I'm learning JavaScript
```

`textContent` will also include the content of elements like **`<script>` and `<style>`**.

If you try to replace the value of `textContent` on a node, it will remove all its child nodes and replace them with a single text node containing the new string:

```javascript
const container = document.getElementById("container");
container.textContent = "Hello, World!";
```

---

## And finally, let's talk about how `textContent` and `innerText` differ from `innerHTML`

Remember that with `innerHTML` you can set the inner HTML content of an element. This is helpful for injecting new HTML into the DOM dynamically.

However, remember that this poses a **security risk** if you don't have control over the string, such as strings containing **data entered by the user**. If that data is malicious, it can lead to serious security issues.

To avoid this, it's recommended to use the **`textContent`** property to insert plain text instead.

The `innerText`, `textContent`, and `innerHTML` properties in JavaScript provide different ways to access and manipulate the content of HTML elements. You should understand the differences between these properties if your goal is to work with HTML content in JavaScript effectively.




