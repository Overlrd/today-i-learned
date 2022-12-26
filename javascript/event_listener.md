# Event Listener in JavaScript

A very useful faeture in JavaScript to deal with user interactions is the event listener.
The event listner can be used to listen at least any action perfomed by a user(click,scroll,hover,...) and respond to the specific action.

## syntax 
```js
addEventListener(type, listener)
addEventListener(type, listener, options)
addEventListener(type, listener, useCapture)
```

 The ```type ``` is a string representing the event type to listen for .
 
 
 The ```listener``` The object that receives a notification (an object that implements the Event interface) when an event of the specified type occurs.
 
 
 The ```options ``` An object that specifies characteristics about the event listener, view [doc](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#parameters). 
 
## Event Listener - examples

#### On DOM Content Loaded
The DOM is the tree-like structure of the webpage , including all the content of the web page.
This is common and necessary to wait for the DOM to have loaded before excuting any JavaScript code.
This can be done via adding an event listener directly to the document and listen for when it finished loading

```js
document.addEventListener('DOMContentLoaded', function(){
document.querySelector('div_1').style.display = 'block':
document.querySelector('div_2').style.display = 'none';
})
```
Here we listen for the DOM content to be loaded then execute a function to hide a div and show another one.

#### On mouse hover
one of the simplest user action to monitor is when the mouse hover an element(a div in this expl)
You can find the element using the queryselector method and then add an event listener to it.

```js
div = document.querySelector('class_of_div');
div.addEventListener('mouseover', function(){
	div.style.cursor = 'pointer';
})
```

In this example we listen for when the user hover the div with his mouse and then specify a function to excute.
the function will set the mouse cursor to pointer to make the user know he can click on the div.

#### On click
now that the user is invited to click the div , we have to listen for when he does and give a response .

```js
div = document.querySelector('class_of_div');
div.addEventListener('click', function(){
	div.style.color = 'red';
}) 
```

## References :
- [EventTarget.addEventListener() - Web APIs | MDN](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener)
