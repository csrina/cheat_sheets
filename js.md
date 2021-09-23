# JS cheat sheet

## `this`

fml https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this

A property of an execution context (global, function or eval) that, in non–strict mode, is always a reference to an object and in strict mode can be any value.

## `function`

!!!!! todo https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions

## `Document`

 - The Document interface represents any web page loaded in the browser and serves as an entry point into the web page's content, which is the DOM (Document Object Model) tree.
 - https://developer.mozilla.org/en-US/docs/Web/API/Document

### `.querySelector(query)`

- returns the first element within the document that matches the selectors given
- exmaple: `var el = document.querySelector(".myclass");`
- https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector

### `.querySelectorAll(query)`

- The Document method querySelectorAll() returns a static (not live) NodeList representing a list of the document's elements that match the specified group of selectors
- https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll
- example: `elementList = document.querySelectorAll('.classname');`

## DOMTokenList

### `.add(DOMString)`

- The add() method of the DOMTokenList interface adds the given token to the list
- example: `tokenList.add(token1[, token2[, ...tokenN]]);`

## Element

### `.classlist`

- The Element.classList is a read-only property that returns a live `DOMTokenList` collection of the class attributes of the element. This can then be used to manipulate the class list.
- https://developer.mozilla.org/en-US/docs/Web/API/Element/classList
- see related methods
  - [.classlist.add('new class name')](#adddomstring)
- example:

```js
    let span = document.querySelector("span");
    let classes = span.classList;
    classes.add("d");
    span.textContent = classes;
```

## `HTMLMediaElement`

### `.play()`

- The HTMLMediaElement play() method attempts to begin playback of the media. It returns a Promise which is resolved when playback has been successfully started.
- https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/play
- example: `htmlMediaElement.play();`
  
### `.currentTime`

- on media elements
- The HTMLMediaElement interface's currentTime property specifies the current playback time in seconds.
- Changing the value of currentTime seeks the media to the new time.
- https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/currentTime
- example: `htmlMediaElement.currentTime = 35;`

## `Window`

- A global variable, window, representing the window in which the script is running, is exposed to JavaScript code.
- https://developer.mozilla.org/en-US/docs/Web/API/Window


## EventListener

### `addEventListener(eventlistener, function) `

- Adds a handler for the an event by providing a callback function.
- https://developer.mozilla.org/en-US/docs/Web/API/EventListener#properties
- eventlistener
  - string
  - the event to listen to on that object
  - exmaples:
  - `'click'`
  - `'keyup'`
  - `'keydown'`
  - [`'transitionend'` - transition event](#transitionevent)
- example

```js
    window.addEventListener('keydown', function(event) {
        console.log(event)
    });
```

### TransitionEvent

https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/transitionend_event

##### .propertyName

- ead-only property of TransitionEvent objects is a DOMString containing the name of the CSS property associated with the transition.
- https://developer.mozilla.org/en-US/docs/Web/API/TransitionEvent/propertyName
- syntax: `name = TransitionEvent.propertyName`
- example: `event.propertyName !== 'transform'`

## NodeList

### `.forEach()`

- method of the NodeList interface calls the callback given in parameter once for each value pair in the list, in insertion order.
- syntax: `list.foreach(callback[, thisArg])`
- parameters:
  - `callback` -A function to execute on each element of someNodeList. It accepts 3 parameters:
    - `currentValue`: The current element being processed in someNodeList
    - `currentIndex`: Optional - The index of the currentValue being processed in someNodeList.
    - `listObj`: Optional - The someNodeList that forEach() is being applied to.
  - `thisArg`: Optional - Value to use as `this` when executing callback
- returns: `undefined`
- exmple: `keys.forEach(key => console.log(key))`
