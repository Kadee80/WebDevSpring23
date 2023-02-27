# The DOM  –  Document Object Model

[Read this article](https://css-tricks.com/dom/) from CSS Tricks. It explains what the DOM is and what it is not, but often confused with.

The Document Object Model is a programming interface for HTML. An HTML document is available for us to manipulate as an object, and this object is structured like a tree.

In the HTML DOM (Document Object Model), everything is a node:

* The document itself is a document node
* All HTML elements are element nodes
* All HTML attributes are attribute nodes
* Text inside HTML elements are text nodes
* Comments are comment nodes

## Document Object

> When an HTML document is loaded into a web browser, it becomes a document object.

>The document object is the root node of the HTML document and the “owner” of all other nodes:
(element nodes, text nodes, attribute nodes, and comment nodes).

>The document object provides properties and methods to access all node objects, from within JavaScript.

>Using the DOM and Javascript we can access any element as long as we navigate parent and child nodes properly. We can create new elements, modify existing elements, and and remove CSS classes and styles, ad or remove attributes, and even destroy existing elements on the page. We do this by accessing the Document Object.

>– W3 Schools DOM Document Object

### The Document Object has many methods for selecting elements:
```javascript
document.getElementById(“IDname” ); 
```
– returns a single element on the page with the ID searched for.
```javascript
document.getElementsByTagName (“P”);
```
– returns an array of elements on the page that match that tag.

```javascript
document.getElementsByClassName(“.active”); 
```
– returns an array of elements on the page that match the CSS class searched for

```javascript
document.querySelector(“.brand”); 
```
– returns the first element on the page that  matches the CSS selector searched for

```javascript
document.querySelectorAll(“.brand”); 
```
– returns and array of all elements on the page that match the CSS selector searched for.