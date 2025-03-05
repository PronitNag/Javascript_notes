# Event Flow in JavaScript

When a JavaScript event occurs, the event is propagated or travels either from the target where the event occurred to the outermost element in the DOM or vice versa.

For example, let's say you click a button on a page. By clicking the button, you've also clicked its parent element and any element the button is inside within the DOM hierarchy.

## Event Bubbling

This is when the event is first registered on the target (or specified element) on which the event happened, and then registered outwards to the parent and onwards to the outermost element.

### Example:

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Event bubbling DEMO</title>
    </head>
    <body>
        <div id="outer">
            <div id="inner">
              <button id='btn'>Click Here</button>
            </div>
        </div>
    </body>
</html>
```

The example here contains a button `#btn`. With event bubbling, when an event occurs (say a click) on the button, the event goes through the following sequence:

1. Button (`#btn`)
2. Inner div (`#inner`)
3. Outer div (`#outer`)
4. Body
5. HTML
6. Document

The event starts to bubble up from the target element back to the outermost ancestor.

## Event Capturing

Event capturing is the opposite of event bubbling. The event starts from the outermost ancestor element and travels down the DOM tree to the target element.

During the capturing phase, event listeners attached to elements are executed in the order of the hierarchy from the topmost ancestor to the target element.

### Example:

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Event bubbling DEMO</title>
    </head>
    <body>
        <div id="outer">
            <div id="inner">
              <button id='btn'>Click Here</button>
            </div>
        </div>
    </body>
</html>
```

Let's add event listeners to the button, the `#inner` div, and the `#outer` div:

```javascript
const button = document.getElementById('btn')
const innerDiv = document.getElementById('inner')
const outerDiv = document.getElementById('outer')

button.addEventListener('click', function() {
  console.log('Click on button')
})

innerDiv.addEventListener('click', function() {
  console.log('Click on inner Div')
})

outerDiv.addEventListener('click', function() {
  console.log('Click on outer Div')
})
```

By default, browsers use the event bubbling approach. So there is no need to add any argument to the event listener. This is the order in which the event handlers will run in response to a click on the button:

1. Button (`#btn`)
2. Inner div (`#inner`)
3. Outer div (`#outer`)

To use the event capturing model, you need to pass a third argument `true` to the event listener.

```javascript
const button = document.getElementById('btn')
const innerDiv = document.getElementById('inner')
const outerDiv = document.getElementById('outer')

button.addEventListener('click', function() {
  console.log('Click on button')
}, true)

innerDiv.addEventListener('click', function() {
  console.log('Click on inner Div')
}, true)

outerDiv.addEventListener('click', function() {
  console.log('Click on outer Div')
}, true)
```

The order for executing the event handlers will now run in the opposite direction, like this:

1. Outer div (`#outer`)
2. Inner div (`#inner`)
3. Button (`#btn`)

## The Event `stopPropagation()` Method

You've learned about how event bubbling registers an event on an element and continues registering the event all the way to the outermost ancestor element. You've also seen how event capturing does the opposite.

But what if you don't want the event to register on all the ancestors? That's where the `stopPropagation` method comes in. You can use this method to prevent the event from propagating through the whole DOM.

### Example:

```javascript
button.addEventListener('click', function(event) {
  event.stopPropagation()
  console.log('Click on button')
})

innerDiv.addEventListener('click', function() {
  console.log('Click on inner Div')
})

outerDiv.addEventListener('click', function() {
  console.log('Click on outer Div')
})
```

Now, only the event handler on the button is fired. The ones on the `innerDiv` and `outerDiv` are not because of the `stopPropagation` method on the button.

Also, note that to get the event object, you need to pass it as an argument to the event handler function.

