# How to Traverse the DOM

To traverse the DOM means to move between the different elements/nodes within the HTML document. This may include selecting or accessing parent, child, or sibling elements (or nodes). You do this to get information or manipulate the document structure.

Before we get into how to traverse the DOM, you need to understand the difference between nodes and elements.

## Difference Between a Node and an Element

Nodes are the building blocks of the DOM. They represent different components in the HTML structure.

Elements are a specific type of node, but not all nodes are elements. Other types of content like attributes of elements, text content, and comments within the code are nodes too. But they are not elements.

An element is a specific type of node that defines the structure of the document's content. Think of elements as the familiar HTML tags you use. Examples include `<div>`, `<p>`, and `<ul>`. Each element can consist of attributes, text content, and other nested elements.

## Selecting a Parent with `parentNode` vs `parentElement`

When it comes to selecting the parent of a DOM element, you can use either the `parentNode` or `parentElement`. Both will get the parent of the element you pass to it.

From a practical viewpoint, the parent of an element or a node will always be an element. So it doesn't matter which one you use; you will get the right parent of the selected element.

### Example:

```html
<div class="container">
  <p class="full-text">
      <i id="italics">Some italicized text</i>
  </p>
</div>
```

```js
const italicizedText = document.getElementById('italics');

console.log(italicizedText.parentNode);
console.log(italicizedText.parentNode.parentNode);
```

First, you select the element. Then, you chain the `parentNode` method to it to get the parent. You can also chain another `parentNode` property to get the parent of a parent element like in the second log statement.

## Selecting Elements with `childNodes` vs `children`

You can select the contents of an element using both the `.childNodes` and `.children` properties. But they work differently.

- **`childNodes`**: returns a `NodeList` of all the child nodes within the selected element. It will include elements and non-element nodes like text nodes, comment nodes, and so on.
- **`children`**: returns an `HTMLCollection` of only the child elements (element nodes) of the selected objects. It will not include any non-element nodes like texts or comments.

### Example:

```html
<div id="container">
  A text node
  <p>Some paragraph</p>
  <!-- This is a comment -->
  <span>Span Element</span>
</div>
```

```js
const container = document.getElementById('container');

const containerChildNodes = container.childNodes;
const containerChildren = container.children;

console.log(containerChildNodes);
console.log(containerChildren);
```

`childNodes` will return all the child nodes (both elements and non-elements). It also includes the whitespaces between elements as text nodes. This can be confusing to work with, so unless you have a good reason not to, you should stick with the `.children` property.

## Selecting the First or Last Child/Element

If you need to select only the first/last child or element, you can use these four properties:

- `firstChild`: Selects only the first child node of the parent element.
- `lastChild`: Selects only the last child node of the parent element.
- `firstElementChild`: Selects only the first child element of the parent.
- `lastElementChild`: Selects only the last child element of the parent.

### Example:

```html
<div id="container">
  A text node
  <p>Some paragraph</p>
  <!-- This is a comment -->
  <span>Span Element</span>
</div>
```

```js
const container = document.getElementById('container');

console.log("FIRST CHILD:", container.firstChild);
console.log("LAST CHILD:", container.lastChild);
console.log("FIRST ELEMENT:", container.firstElementChild);
console.log("LAST ELEMENT:", container.lastElementChild);
```

Note how `firstChild` returns the first text node but `firstElementChild` returns the first paragraph instead. This means it ignored the text node that comes before the paragraph.

## Selecting a Sibling of Nodes in the DOM

You've learned how to select a parent or a child of an element. You can also select a sibling of an element using the following properties:

- `nextSibling`: Selects the next node within the same parent element.
- `nextElementSibling`: Selects the next element, and ignores any non-element nodes.
- `previousSibling`: Selects the previous node within the same parent element.
- `previousElementSibling`: Selects the previous element, and ignores any non-element nodes.

### Example:

```html
<div>
  <p id="one">First paragraph</p>
  text node
  <p id="two">Second paragraph</p>
  another text node
  <p id="three">Third paragraph</p>
  <p id="four">Fourth paragraph</p>
</div>
```

```js
const paragraphTwo = document.getElementById('two');

console.log("nextSibling: ", paragraphTwo.nextSibling);
console.log("nextElementSibling: ", paragraphTwo.nextElementSibling);
console.log("previousSibling: ", paragraphTwo.previousSibling);
console.log("previousElementSibling: ", paragraphTwo.previousElementSibling);
```

`nextSibling` and `previousSibling` select the text nodes because they consider all nodes within the parent. Meanwhile, `nextElementSibling` and `previousElementSibling` select only the paragraph elements because they ignore non-element nodes like text.

