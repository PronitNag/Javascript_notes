# DOM Events and Event Listeners

DOM events are actions that take place in the browser. These events allow you to make websites interactive.

Some DOM events are user-initiated like clicking, moving the mouse, or typing on the keyboard. Others are browser-initiated like when a page finishes loading.

## Difference Between Event Listener and Event Handler

An **event listener** is a method that lets you know when an event has taken place. It allows you to "listen" or keep an eye out for DOM events. That way, when an event happens, you can do something.

An **event handler** is a response to the event. It's a function that runs when an event occurs.

For example, you can attach an event listener to a button that lets you know when a user clicks that button. Then you can write an event handler (a function) that prints something on screen anytime a click event occurs.

```javascript
const button = document.querySelector('button');
button.addEventListener('click', function() {
  console.log("Button clicked!");
});
```

In this case, the event listener informs your app when a click occurs and then triggers a response. The function that runs when the click occurs is an example of an event handler.

## Three Ways to Register Events in JavaScript

The following are three different ways you can listen to and respond to DOM events using JavaScript.

### 1. Using Inline Event Handlers

This is when you add the event listener as an attribute to HTML elements.

```html
<button onclick="alert('Hello')">Click me!</button>
```

### 2. Using On-Event Handlers

This method assigns a function to an event property.

```html
<button>Click me!</button>

<script>
  const myButton = document.querySelector('button');

  myButton.onclick = function() {
    console.log("Run first handler");
  };

  myButton.onclick = function() {
    console.log("Run second handler");
  };
</script>
```

> Only the second event handler will execute because it overrides the first one.

### 3. Using the `addEventListener` Method

This method allows you to attach multiple event handlers to an element, and they execute in the order they were added.

```html
<button>Click me!</button>

<script>
  const myButton = document.querySelector('button');

  myButton.addEventListener('click', function() {
    console.log("Run first handler");
  });

  myButton.addEventListener('click', function() {
    console.log("Run second handler");
  });
</script>
```

> The `addEventListener` method executes both event handlers.

## Practice Challenge

### Challenge

Consider the following HTML and CSS code. The challenge includes two elements: a `#gift-box` div and a `#click-btn` button. The gift box is hidden with the `.hide` class.

Your task is to write JavaScript code that listens to a click event on the button and displays the hidden box when the user clicks the button.

```html
<!DOCTYPE html>
<html lang="en">
  <head></head>
  <body>
      <div id="gift-box" class="hide">🎁</div>
      <button id="click-btn">Show the box</button>
  </body>
</html>
```

```css
.hide {
  display: none;
}

#gift-box {
  font-size: 5em;
}
```

### Solution

```javascript
const giftBoxElement = document.getElementById('gift-box');
const buttonElement = document.getElementById('click-btn');

buttonElement.addEventListener('click', function() {
  giftBoxElement.classList.remove('hide');
});
```

## The Event Object

This is a JavaScript object the browser passes as an argument to the event handler function anytime an event occurs. It includes some useful properties and methods such as:

- `type`: The type of event that occurred (e.g., `click`, `mouseover`, `keydown`).
- `target`: The element on which the event occurred.
- `clientX` and `clientY`: The horizontal and vertical coordinates of the mouse pointer at the time the event occurred.
- `preventDefault()`: Prevents default actions associated with events (e.g., preventing a form submission on the `submit` event).
- `stopPropagation()`: Prevents the event from propagating through the DOM.

## Types of Events

There are many different kinds of DOM events. Here are a few common ones:

### Mouse Events
- `click`: When the element is clicked.
- `dblclick`: When the element is double clicked.
- `mouseover`: When the mouse pointer enters the element.
- `mouseleave`: When the mouse pointer leaves the element.
- `mousedown`: When the mouse is pressed down over an element.
- `mouseup`: When the mouse is released over an element.

### Keyboard Events
- `keydown`: When a key on the keyboard is pressed down.
- `keyup`: When a key on the keyboard is released.
- `keypress`: When a key is pressed (deprecated in modern browsers).

### Form Events
- `submit`: When a form is submitted.
- `input`: When the value of an input field changes.
- `change`: When the value of a form element changes and loses focus.

### Window Events
- `load`: When the browser finishes loading the page.
- `unload`: When the user leaves the page.
- `resize`: When the browser window is resized.
- `scroll`: When the user scrolls through the document.

For a comprehensive list of DOM events, check the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/Events).

