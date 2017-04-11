# DOM Cheatsheet

## Selecting Elements
- **getElementById**: get an element that has the provided Id.
- **getElementsByClassName**: gets a nodelist (nodelist is not an array, rather it is array-like object) by providing a class name.
- **getElementsByTagName** to get a nodelist by the provided tag name.
- **querySelector**: returns the first matching Element node within the node's subtree. you can pass in any css style selector (jquery style) as an argument, including tags, classes, or IDs can be passed to `querySelector`. You can also pass in complex CSS selectors like `document.querySelector('p .red')`
```js
document.querySelector('.red'); // would return the first node that has the 'red' class.
document.querySelector('p'); // would return the first paragraph tag.
document.querySelector('p .red') //  would get you the first paragraph with a 'red' class.
```
- **querySelectorAll**: returns a NodeList containing all matching Element nodes within the node's subtree, or an empty NodeList if no matches are found

## Event Listeners
- **addEventListener**: adds a listnere to any element. takes two arguments: the first is the type of the event, and the second is a callback function to execute when that event occurs.

Documentation for addEventListener: [DOM addEventListener](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)

```js
var myButton = document.getElementById('btn-1');
// Console log everytime the button is clicked:
myButton.addEventListener('click', () => {
  console.log('You clicked the button!')
})
// Alert the text of the button anytime you move your mouse over it
myButton.addEventListener('mouseover', (event) => {
  alert('You scrolled over button ' + event.target.innerHTML)
})
```
## Event Types
Full reference of all DOM event types: [DOM Events Reference](https://developer.mozilla.org/en-US/docs/Web/Events)

Common events:
- click
- keydown/keyup
- mouseenter/mouseleave/mouseover
- scroll
- focus

## Creating Elements
- **createElement** takes in the name of an element as an argument, and creates a new DOM node for that element. For example, `document.createElement('li')` would create a new `li` node.
- **createDocumentFragment** creates a DOM subtree, that you can then append elements to. You can then later append the entire subtree to the DOM. this helps with efficiency and performance. For example:
```js
var subTree = document.createDocumentFragment();
for(var i = 0; i < 100; i++) {
    var newListItem = document.createElement('li');
    newListItem.innerHTML = 'Item' + i;
    subTree.appendChild(newListItem);
}
document.body.appendChild(subTree);
// in this example, we only append one element to the actual DOM
// if we didn't use a document fragment, we would need to append all 100 list items directly to the DOM
// which would be inefficient and could slow down the browser
```

## Adding and Removing Elements
- **appendChild** adds a new child node as the last child of a parent
- **insertBefore** takes two arguments: an existing node, and a new node to insert before it
- **removeChild** deletes a child node
- **replaceChild** takes two arguments: a new node, and the old node it should replace

```js
var firstParagraph = document.createElement('p');
var secondParagraph = document.createElement('p');
document.body.appendChild(firstParagraph);
document.body.replaceChild(secondParagraph, firstParagraph);
document.body.removeChild(secondParagraph);
```


## Changing Attributes, Classes, and IDs
- **getAttribute** takes in the name of an attribute, and returns the value
- **setAttribute** takes in two arguments: the name of an attribute, and a new value. sets the attribute to the new value
- **attributes** property (not a method) that holds a collection of all attributes for a particular node
- **className** property (not a method) that contains all of an element's classes

```js
var input1 = document.getElementById("input1");
var inputType = input1.getAttribute("type");

alert(inputType); // shows the value of type for the element with id="input1"

// set input1's 'type' attribute to 'text'
input1.setAttribute('type', 'text');

// Get the first <p> element in the document
var para = document.getElementsByTagName("p")[0];
var atts = para.attributes; // returns collection of all attributes

para.className = 'red'; // adds the 'red' class to the paragraph tag. this will overwrite any existing classes
```


## Interview Questions
- youre given HTML with a list of 100 items. whenever you click on one of the items, you should console.log `'You just clicked a list item ' + the text of the list item that you clicked`
- given an input tag and a submit button, add a new list item to the page whenever someone enters something into the input tag and hits submit
- youre given HTML for a list with five items, and a button. whenever you click the button, one of the list items should be removed from the page
- youre given an HTML form with three input fields: firstname, lastname, and phone number. when the form is submitted, console log: `You can reach {firstname} {lastname} at {phonenumber}`, using the actual results from the input.
- How could you capture ALL clicks on a page, and send an alert that says `'You clicked element ' + the name of the clicked element` whenever any element is clicked?
- Write a function that traverses the DOM tree and prints out the innerHTML of each element


## Resources
- [DOM Interview Questions](http://www.thatjsdude.com/interview/dom.html#fastestDOMQuery)
- [Query Selectors](https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Locating_DOM_elements_using_selectors)
- [DOM addEventListener](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)
- [DOM Events Reference](https://developer.mozilla.org/en-US/docs/Web/Events)
