# Selecting DOM

# Selecting DOM Elements in JavaScript

When working with the Document Object Model (DOM) in JavaScript, you often need to select elements to manipulate them. Here are different methods to do so:

## 1. `document.getElementById()`
- Selects an element by its `id` attribute.
- Returns a **single** element (or `null` if not found).
- Example:
  ```javascript
  let element = document.getElementById("myId");
  console.log(element);
  ```

## 2. `document.getElementsByClassName()`
- Selects elements by their `class` name.
- Returns a **live HTMLCollection** (array-like but not an array).
- Example:
  ```javascript
  let elements = document.getElementsByClassName("myClass");
  console.log(elements[0]); // Access first element
  ```

## 3. `document.getElementsByTagName()`
- Selects elements by their tag name (`div`, `p`, `span`, etc.).
- Returns a **live HTMLCollection**.
- Example:
  ```javascript
  let elements = document.getElementsByTagName("p");
  console.log(elements.length); // Number of paragraphs
  ```

## 4. `document.querySelector()`
- Selects the **first** matching element using a CSS selector.
- Returns a **single element** (or `null` if not found).
- Example:
  ```javascript
  let element = document.querySelector(".myClass");
  console.log(element);
  ```

## 5. `document.querySelectorAll()`
- Selects **all** matching elements using a CSS selector.
- Returns a **NodeList** (static, unlike live HTMLCollection).
- Example:
  ```javascript
  let elements = document.querySelectorAll("div.myClass");
  console.log(elements.length); // Number of matched elements
  ```

### Summary Table
| Method                      | Returns                 | Live Update? | Selector Type  |
|-----------------------------|-------------------------|-------------|---------------|
| `getElementById("id")`       | Single Element (`null` if not found) | No  | `id` |
| `getElementsByClassName("class")` | HTMLCollection         | Yes | `class` |
| `getElementsByTagName("tag")`  | HTMLCollection         | Yes | `tag` |
| `querySelector("selector")`   | Single Element (`null` if not found) | No | CSS Selector |
| `querySelectorAll("selector")` | NodeList               | No | CSS Selector |

These methods allow developers to efficiently access and manipulate HTML elements in a webpage.
