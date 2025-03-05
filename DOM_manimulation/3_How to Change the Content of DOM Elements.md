# How to Change the Content of DOM Elements

So far you've learned about different ways to select DOM elements. But that is only the beginning. Now, let's see how you can manipulate the DOM to change the content of a webpage.

The first thing you need to do is to select the element. You can do that using any of the methods you learned from the previous section.

After selecting the element, there are several methods you can use to add or update the content.

## The `innerHTML` Property

This is a method that allows you to read or update both the structure and content of elements. Let's see an example of how you can use the `innerHTML` method.

The following is some markup of three paragraphs, each with an `id`:

```html
<p id="topic">JS array methods</p>
<p id="first-method">map</p>
<p id="second-method">filter</p>
```

You can read or get the content of any of the paragraphs using `innerHTML`. For example, let's get the content of the first paragraph:

```javascript
const topicElement = document.querySelector('#topic');
console.log(topicElement.innerHTML);
```

Now, let's say you want to update the topic from "JS array methods" to "JavaScript array methods". You can do that by assigning the new text to the `innerHTML` of the element:

```javascript
const topicElement = document.querySelector('#topic');
topicElement.innerHTML = "JavaScript array methods";
```

With `innerHTML`, you can change more than just the content. You can also change the HTML structure of the element. For example, if you want to make the word "JavaScript" bold, you could do this:

```javascript
topicElement.innerHTML = "<b>JavaScript</b> array methods";
```

## Security Risks With `innerHTML`

Using `innerHTML` poses potential security risks. An example is cross-site scripting (XSS) attacks.

If the content you're inserting comes from user input or any untrusted source, be sure to validate and sanitize it before using `innerHTML` to prevent XSS attacks. You can use a library like [DOMPurify](https://github.com/cure53/DOMPurify) to do this.

Also, if you are working with plain text content, consider using methods like `innerText` and `textContent`.

## The `innerText` and `textContent` Properties

Both `innerText` and `textContent` ignore HTML tags and treat them as part of a string. You can use both methods to read or update the text of DOM elements.

A key difference between the two is in how they treat the text. Using `innerText` returns the text as it appears on the screen. Using `textContent` returns text as it appears in the markup. Let's see an example below.

```html
<p>Key =<span style="display: none;"> ABC123</span></p>
```

The example includes a paragraph element. Inside the paragraph is a span that contains a key. The key does not appear on screen because its inline style is set to `display: none`.

Now, let's select the paragraph and print both the `innerText` value and `textContent` value to see the difference:

```javascript
const paragraph = document.querySelector('p');

console.log("innerText: ", paragraph.innerText);
console.log("textContent: ", paragraph.textContent);
```

Note how `innerText` returns the text as it appears on the screen (without the value of the key which is hidden with CSS). And note how `textContent` returns the text including hidden elements and whitespaces.

Let's see another example for adding text to an element. The following code includes two paragraphs, each with bold text and an empty span, as well as a horizontal line between them:

```html
<p>
  <b>innerText Example</b>
  <span id="inner-text"></span>
</p>

<hr>    

<p>
  <b>textContent Example</b>
  <span id="text-content"></span>
</p>
```

Now, let's select the two span elements and add the same text to them. This will help you better understand the difference between `innerText` and `textContent`.

```javascript
const example1 = document.querySelector('#inner-text');
const example2 = document.querySelector('#text-content');

let address = `
  ABC Street,
  Spintex Road,
  Accra,
  Ghana.
`;

example1.innerText = address;
example2.textContent = address;
```

The code gives the same variable `address` to the two examples. The first uses `innerText` and the second uses `textContent`. See the results below:

Notice how `innerText` uses the line breaks but the `textContent` example doesn't.

Another key difference between the two methods is how they behave when used inside loops. `innerText` can be slower than `textContent` when dealing with bulk operations or frequent updates in a loop.

Read this [freeCodeCamp article](https://www.freecodecamp.org/news/javascript-innerhtml-vs-innertext-vs-textcontent/) to learn more about the difference between `innerHTML`, `innerText`, and `textContent`.




