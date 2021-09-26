# JS cheat sheet

## todo

[Using_dynamic_styling_information](https://developer.mozilla.org/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)

[`this`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)
A property of an execution context (global, function or eval) that, in non–strict mode, is always a reference to an object and in strict mode can be any value.

[`function`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)

## Random

`const [last, first] = lastOne.split(', ')`

- `lastOne` is a name in format `last, first`
- its split on the `', '`
- then stored into 2 variables `last` and `first`
- not sure what this would be called

## `Document`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/Document)
The Document interface represents any web page loaded in the browser and serves as an entry point into the web page's content, which is the DOM (Document Object Model) tree.

### `.querySelector(query)`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)

- returns the first element within the document that matches the selectors given
- exmaple: `var el = document.querySelector(".myclass");`
- how to query
  - clase: `.classsName`
  - id: `#id`

### `.querySelectorAll(query)`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll)

- The Document method querySelectorAll() returns a static (not live) NodeList representing a list of the document's elements that match the specified group of selectors
- example: `elementList = document.querySelectorAll('.classname');`

### `.documentElement`

grab the root element of the html file.

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/Document/documentElement)

exmaple: `document.documentElement`

#### `.style` (documentElement)

grabs the style element from the root html element in the document.

Example: `document.documentElement.style`

#### `.setProperty`

used to set the value of a css property.

Example: `document.documentElement.style(elementName, newValue)`

## DOMTokenList

### `.add(DOMString)`

- The add() method of the DOMTokenList interface adds the given token to the list
- example: `tokenList.add(token1[, token2[, ...tokenN]]);`

### `.toggle(token)`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/DOMTokenList/toggle)

- method that removes a given `token` from the list and returns `false`. If `token` doesn't exist it's added and the function returns `true`.

**Syntax**: `tokenList.toggle(token [, force]);`

**Parameters**:

- `token` : A DOMString representing the token you want to toggle.
- `[force]`: If included, turns the toggle into a one way-only operation. I
  - `false`, then token will only be removed, but not added
  - `true`, then token will only be added, but not removed

**Return value**: `true` or `false`, indicating whether token is in the list after the call.
## Element

### `.classlist`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/Element/classList)

- The Element.classList is a read-only property that returns a live `DOMTokenList` collection of the class attributes of the element. This can then be used to manipulate the class list.
- see related methods
  - [.classlist.add('new class name')](#adddomstring)
    - example:

    ```js
        let span = document.querySelector("span");
        let classes = span.classList;
        classes.add("d");
        span.textContent = classes;
    ```

  - [.classlist.toggle('class-name')](#toggletoken)
    - exmple: `document.querySelector("span").classList.toggle('class-name')`

## HTMLElement

### `.style` (HTMLELement)

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/style)

The style read-only property returns the inline style of an element in the form of a CSSStyleDeclaration object that contains a list of all styles properties for that element with values assigned for the attributes that are defined in the element's inline style attribute.

**Syntax** - `style = element.style`

**Setting styles** - While this property is considered read-only, it is possible to set an inline style by assigning a string directly to the style property. In this case the string is forwarded to CSSStyleDeclaration.cssText. Using style in this manner will completely overwrite all inline styles on the element.

Therefore, to add specific styles to an element without altering other style values, it is generally preferable to set individual properties on the CSSStyleDeclaration object. For example, element.style.backgroundColor = "red".

### `.dataset`

puts all user defined html props (those starting with `dataset-`) into an object that is easily accessible.

example: `element.datatset.attributeName`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/dataset)

## `HTMLMediaElement`

### `.play()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/play)

- The HTMLMediaElement play() method attempts to begin playback of the media. It returns a Promise which is resolved when playback has been successfully started.
- example: `htmlMediaElement.play();`
  
### `.currentTime`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/HTMLMediaElement/currentTime)

- on media elements
- The HTMLMediaElement interface's currentTime property specifies the current playback time in seconds.
- Changing the value of currentTime seeks the media to the new time.
- example: `htmlMediaElement.currentTime = 35;`

## `Window`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/Window)

A global variable, window, representing the window in which the script is running, is exposed to JavaScript code.

### `setInterval()`

The setInterval() method, offered on the Window and Worker interfaces, repeatedly calls a function or executes a code snippet, with a fixed time delay between each call.

`var intervalId = setInterval(func, [delay, arg1, arg2, ...]);`

- Parameters
  - `func` - A function to be executed every delay milliseconds. The first execution happens after delay milliseconds.
  - \[`delay`\] - The time, in milliseconds (thousandths of a second), the timer should delay in between executions of the specified function or code. See Delay restrictions below for details on the permitted range of delay values.
  - \[`arg1, ..., argN`\]- Additional arguments which are passed through to the function specified by func once the timer expires.
- Return value - The returned intervalID is a numeric, non-zero value which identifies the timer created by the call to `setInterval()`; this value can be passed to `clearInterval()` to cancel the interval.

## DATE

[dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

JavaScript Date objects represent a single moment in time in a platform-independent format. Date objects contain a Number that represents milliseconds since 1 January 1970 UTC.

### Constructors

#### `Date()`

When called as a function, returns a string representation of the current date and time, exactly as `new Date().toString()` does.

#### `new Date()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/Date)

When called as a constructor, returns a new `Date` object.

**Syntax:**

```js
new Date()
new Date(value)
new Date(dateString)

new Date(year, monthIndex)
new Date(year, monthIndex, day)
new Date(year, monthIndex, day, hours)
new Date(year, monthIndex, day, hours, minutes)
new Date(year, monthIndex, day, hours, minutes, seconds)
new Date(year, monthIndex, day, hours, minutes, seconds, milliseconds)
```

**Parameters:**

1. No parameters - newly-created Date object represents the current date and time as of the time of instantiation.
2. Time value or timestamp number
   1. `value` - An integer value representing the number of milliseconds since January 1, 1970, 00:00:00 UTC (the ECMAScript epoch, equivalent to the UNIX epoch), with leap seconds ignored.
3. Timestamp string `dateString` - A string value representing a date, specified in a format recognized by the Date.parse() method.
4. Individual date and time component values - Given at least a year and month, this form of Date() returns a Date object whose component values (year, month, day, hour, minute, second, and millisecond) all come from the following parameters. Any missing fields are given the lowest possible value (**1 for day and 0 for every other component**). The parameter values are all **evaluated against the local time zone, rather than UTC**.
   1. `year` \[Integer\] - Values from 0 to 99 map to the years 1900 to 1999. All other values are the actual year. See the example.
   2. `monthIndex` \[Integer\] - beginning with 0 for January to 11 for December. If a value greater than 11 is passed in, then those months will be added to the date; for example, new Date(1990, 12, 1) will return January 1st, 1991
   3. \[`day`\] \[Integer\] - default is 1.
   4. \[`hours`\] \[Integer\] - between 0 and 23. Defaults to 0.
   5. \[`minutes`\] \[Integer\] - default is 0 minutes past the hour.
   6. \[`seconds`\] \[Integer\] - default is 0 seconds past the minute.
   7. \[`milliseconds`\] \[Integer\] - default is 0 milliseconds past the second.

**Return value:**

1. valid call returns a `Date` object.
2. invalid call returns a `Date` object whose toString() method returns the literal string `Invalid Date`.

### `.getSeconds()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getSeconds)

method returns the seconds in the specified date according to local time.

**Return value:** An integer number, between 0 and 59, representing the seconds in the given date according to local time.

**Example:** `new Date('December 25, 1995 23:15:30').getSeconds();`

### `.getMinutes()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getMinutes)

 method returns the minutes in the specified date according to local time.

**Return value:** An integer number, between 0 and 59, representing the minutes in the given date according to local time.

**Example:** `new Date('December 25, 1995 23:15:30').getMinutes();`

### `.getHours()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getHours)

method returns the hour for the specified date, according to local time.

**Return value:** An integer number, between 0 and 23, representing the hour for the given date according to local time.

**Example:** `new Date('December 25, 1995 23:15:30').getHours();`

## EventListener

### `addEventListener(eventlistener, function)`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/EventListener#properties)

- Adds a handler for the an event by providing a callback function.
- eventlistener
  - string
  - the event to listen to on that object
  - exmaples:
  - `'click'`
  - `'keyup'`
  - `'keydown'`
  - [`'transitionend'` - transition event](#transitionevent)
  - `change`
  - `mousemove`
- example

```js
    window.addEventListener('keydown', function(event) {
        console.log(event)
    });
```

### TransitionEvent

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/transitionend_event)

#### .propertyName

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/TransitionEvent/propertyName)

- read-only property of TransitionEvent objects is a DOMString containing the name of the CSS property associated with the transition.
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

## `Array`

### `.from()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)

- Static method creates a new, shallow-copied Array instance from an array-like or iterable object.
- used to turn a NodeList into an array to use `Array.prototype` methods on it

**Syntax:**

```js
Array.from(arrayLike, (element, index) => { ... } )
Array.from(arrayLike, mapFn, thisArg)
Array.from(arrayLike, function mapFn(element, index) { ... }, thisArg)
```

### `.prototype` (array)

#### `.filter()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

**syntax**:

```js
filter((element, [index], [array]) => { ... } )
filter(callbackFn, thisArg)
filter(function callbackFn(element, index, array) { ... }, thisArg)
```

**Parameters:**

- `callbackFn`: Function is a predicate, to test each element of the array. Return a value that coerces to true to keep the element, or to false otherwise. It accepts three arguments:
  - `element`: The current element being processed in the array.
  - `[index]`: The index of the current element being processed in the array.
  - `[array]`: The array `filter` was called upon.
- `[thisArg]`: Value to use as `this` when executing `callbackFn`.

**Return value** :A new array with the elements that pass the test. If no elements pass the test, an empty array will be returned.

#### `.map()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

The `map()` method creates a new array populated with the results of calling a provided function on every element in the calling array.

**Syntax:**

```js
map((element, [index], [array]) => { ... })
map(callbackFn, thisArg)
map(function callbackFn(element, index, array) { ... }, thisArg)
```

#### `.reduce()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

- The reducer walks through the array element-by-element, at each step adding the current array value to the result from the previous step (this result is the running sum of all the previous steps) — until there are no more elements to add.

**Syntax:**

```js
reduce((previousValue, currentValue) => { ... } )
reduce((previousValue, currentValue, currentIndex, array) => { ... }, initialValue)

reduce(function callbackFn(previousValue, currentValue) { ... })
reduce(function callbackFn(previousValue, currentValue, currentIndex, array) { ... }, initialValue)
```

**Example**: `[0, 1, 2, 3, 4].reduce((previousValue, currentValue, currentIndex, array) => previousValue + currentValue)`

#### `.sort()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

- method sorts the elements of an array in place and returns the sorted array. The default sort order is ascending, built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values.
- If `a` and `b` are two elements being compared, then:
  - If `compareFunction(a, b)` returns a value *> than 0*, sort `b` before `a`.
  - If `compareFunction(a, b)` returns a value *< than 0*, sort `a` before `b`.
  - If `compareFunction(a, b)` returns *0*, `a` and b are considered equal

**Syntax**:

```js
// Functionless
sort() //the array elements are converted to strings, then sorted according to each character's Unicode code point value.

// Arrow function
sort((firstEl, secondEl) => { ... } )

// Inline compare function
sort(function compareFn(firstEl, secondEl) { ... })
```

**Example** : `[4, 2, 5, 1, 3].sort((a, b) => a - b);`

## `console.`

### `.table()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/console/table)

- method displays tabular data as a table.
- This function takes one mandatory argument data, which must be an `array` or an `object`, and one additional optional parameter `columns` is the name of columns to print for objects

**syntax**:

```js
console.table(data);
console.table(data, columns);
```

## `String`

### `.prototype` (string)

#### `.includes()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)

- method performs a case-sensitive search to determine whether one string may be found within another string, returning `true` or `false` as appropriate.

**Syntax**:

```js
includes(searchString)
includes(searchString, position) //position where to start the search
```
