# What is DOM?

The Document part refers to the webpage you see in the browser. 

Object means the elements like images, headers, and paragraphs are treated like objects.

The Model in DOM means it's a representation or copy of the HTML document as a hierarchical tree.

Basically It grabs an HTML page and turns it into a logical tree.

Browser Object Model (BOM). The BOM holds all the methods and properties for JavaScript to interact with the browser. 
- This is information related to previous pages visited, <br />
- the size of the window of the browser, and <br />
- also the DOM. <br />

Attributes influence the element they are specified on. that they modify the element they are specified on. <br />

## DOM vs BOM?

## 🔍 DOM vs. BOM: Key Differences

| Feature  | DOM (Document Object Model) | BOM (Browser Object Model) |
|----------|----------------------------|----------------------------|
| **Definition** | Represents the web page's structure | Represents browser-specific features |
| **Main Object** | `document` | `window` |
| **Usage** | Modify HTML, CSS, and content dynamically | Interact with browser features (e.g., alerts, history, screen size) |
| **Examples** | `document.getElementById()`, `document.querySelector()` | `window.alert()`, `window.location.href`, `history.back()` |

## 🔗 Relationship Between `window` and `document`
- `window` is the **global object** in JavaScript.
- `document` is a **property of `window`** that represents the page content.

### Example:
```js
console.log(window.document); // Same as console.log(document)
