# JS cheat sheet

## todo

[Using_dynamic_styling_information](https://developer.mozilla.org/en-US/docs/Web/API/CSS_Object_Model/Using_dynamic_styling_information)

[`this`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)
A property of an execution context (global, function or eval) that, in non–strict mode, is always a reference to an object and in strict mode can be any value.

[`function`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)

[truthy and falsey](https://developer.mozilla.org/en-US/docs/Glossary/Truthy)

## Random

`const [last, first] = lastOne.split(', ')`

- `lastOne` is a name in format `last, first`
- its split on the `', '`
- then stored into 2 variables `last` and `first`
- not sure what this would be called

### `var` vs `const` vs `let` [fcc](https://www.freecodecamp.org/news/var-let-and-const-whats-the-difference/)

- `var` declarations are globally scoped or function scoped while `let` and `const` are block scoped.
- updates and re-declaration:
  - `var` variables can be updated and re-declared within its scope; 
  - `let` variables can be updated but not re-declared; 
  `const` variables can neither be updated nor re-declared.
- They are all hoisted to the top of their scope. But while `var` variables are initialized with `undefined`, `let` and `const` variables are not initialized.
- While `var` and `let` can be **declared without being initialized**, `const` **must be initialized** during declaration.


## `Document`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/Document)
The Document interface represents any web page loaded in the browser and serves as an entry point into the web page's content, which is the DOM (Document Object Model) tree.

### `.querySelector(query)`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)

- returns the first element within the document that matches the selectors given, returns an [`Element`](#element)
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

### `.innerHTML` - property [dmo] (https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML)

The `Element` property `innerHTML` gets or sets the HTML or XML markup contained within the element. 

**Syntax**

```js 
const content = element.innerHTML; //reading 

element.innerHTML = htmlString; //setting
```

**Value**
A `DOMString` containing the HTML serialization of the element's descendants. Setting the value of `innerHTML` removes all of the element's descendants and replaces them with nodes constructed by parsing the HTML given in the string *htmlString*.

**Exceptions**

- `SyntaxError` `DOMException`
  - Thrown if an attempt was made to set the value of `innerHTML` using a string which is not properly-formed HTML.
- `NoModificationAllowedError` `DOMException`
  - Thrown if an attempt was made to insert the HTML into a node whose parent is a `Document`.


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

### `.from()`- method [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)

- Static method creates a new, shallow-copied Array instance from an array-like or iterable object.
- used to turn a NodeList into an array to use `Array.prototype` methods on it

**Syntax:**

```js
Array.from(arrayLike, (element, index) => { ... } )
Array.from(arrayLike, mapFn, thisArg)
Array.from(arrayLike, function mapFn(element, index) { ... }, thisArg)
```

### `.prototype` (array)

#### `.filter()` [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

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

#### `.map()` - method [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

The `map()` method creates a new array populated with the results of calling a provided function on every element in the calling array.

**Syntax:**

```js
map((element, [index], [array]) => { ... })
map(callbackFn, thisArg)
map(function callbackFn(element, index, array) { ... }, thisArg)
```
**Parameters:**

- `callbackFn` 
  - Function that is called for every element of the array. Each time `callbackFn` executes, the returned value is added to `newArray`.
  - arrguments:
    - `element` - The current element being processed in the array.
    - `[index]`- The index of the current element being processed in the array.
    - `array` - The array map was called upon.
- `[thisArg]` - Value to use as `this` when executing `callbackFn`.

**Return value** A new array with each element being the result of the callback function.

#### `.reduce()` [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

- The reducer walks through the array element-by-element, at each step adding the current array value to the result from the previous step (this result is the running sum of all the previous steps) — until there are no more elements to add.

**Syntax:**

```js
reduce((previousValue, currentValue) => { ... } )
reduce((previousValue, currentValue, currentIndex, array) => { ... }, initialValue)

reduce(function callbackFn(previousValue, currentValue) { ... })
reduce(function callbackFn(previousValue, currentValue, currentIndex, array) { ... }, initialValue)
```

**Example**: `[0, 1, 2, 3, 4].reduce((previousValue, currentValue, currentIndex, array) => previousValue + currentValue)`

#### `.sort()` - method [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

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

#### `.push()` - mehtod [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)

- **Syntax:**
  ```js
    push(element0)
    push(element0, element1)
    push(element0, element1, ... , elementN)
  ```
- **Paramaters:**
  - `elementN`: 1 to n elements to add to the end of the array
- **Returns:**
  - new length of the array, does not return a new array or a copy of it

#### `.join()` - method [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

**Syntax**

```js
join()
join(separator)
```

**Parameters**

- `[separator]` - Specifies a string to separate each pair of adjacent elements of the array. The separator is converted to a string if necessary. If omitted, the array elements are separated with a comma (","). If `separator` is an empty string, all elements are joined without any characters in between them.

**Return value** : A string with all array elements joined. If `arr.length` is 0, the empty string is returned. 

#### `.some()` - method [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)

tests whether at least one element in the array passes the test implemented by the provided function.

- **Syntax**

```js
// Arrow function
some((element, [index], [array]) => { ... } )
// Callback function
some(callbackFn, [thisArg])
// Inline callback function
some(function callbackFn(element, [index], [array]) { ... }, [thisArg])
```

- **Parameters**
  - `callbackFn` - A function to test for each element, taking three arguments:
    - `element` - The current element being processed in the array.
    - `[index]` - The index of the current element being processed in the array.
    - `[array]` - The array `some()` was called upon.
  - `[thisArg]` - A value to use as `this` when executing `callbackFn`.
- **Return value** true if the callback function returns a truthy value for at least one element in the array. Otherwise, false.

#### `.every()` - methods [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every)

tests whether all elements in the array pass the test implemented by the provided function. It returns a Boolean value.

- **Syntax:**

```js
// Arrow function
every((element, [index], [array]) => { ... } )
// Callback function
every(callbackFn, [thisArg])
// Inline callback function
every(function callbackFn(element, [index], [array]) { ... }, [thisArg])
```

- **Parameters:**
  - `callbackFn` - A function to test for each element, taking three arguments
    - `element` - The current element being processed in the array.
    - `[index]` - The index of the current element being processed in the array.
    - `[array]` - The array `every` was called upon.
  - `[thisArg]` - A value to use as `this` when executing `callbackFn`.
- **Return Value:** `true` if the `callbackFn` function returns a *truthy* value for every array element. Otherwise, `false`. 

#### `.find()` - method [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

returns the value of the first element in the provided array that satisfies the provided testing function.

- **Syntax:**

```js
// Arrow function
find((element, [index], [array]) => { ... } )
// Callback function
find(callbackFn, [thisArg])
// Inline callback function
find(function callbackFn(element, [index], [array]) { ... }, [thisArg])
```

- **Parameters:**
  - `callbackFn` - Function to execute on each value in the array, taking 3 arguments:
    - `element` - The current element in the array.
    - `[index]` - The index (position) of the current element in the array.
    - `[array]` - The array that find was called on.
- `[thisArg]` - Object to use as this inside callbackFn.
- **Return Value:**  The *value* of the first element in the array that satisfies the provided testing function. Otherwise, `undefined` is returned.

#### `findIndex()` - method [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

returns the index of the first element in the array that satisfies the provided testing function.

- **Syntax:**

```js
// Arrow function
findIndex((element, [index], [array]) => { ... } )
// Callback function
findIndex(callbackFn, [thisArg])
// Inline callback function
findIndex(function callbackFn(element, [index], [array]) { ... }, [thisArg])
```

- **Parameters:**
  - `callbackFn` - A function to execute on each value in the array until the function returns `true`, indicating that the satisfying element was found. It takes three arguments:
    - `element` - The current element in the array.
    - `[index]` - The index (position) of the current element in the array.
    - `[array]` - The array that findIndex was called on.
- `[thisArg]` - Object to use as this inside callbackFn.
- **Return Value:** The index of the first element in the array that passes the test. Otherwise, -1.

#### `.splice()` - method [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

Changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.

- **Syntax:**

```js
splice(start)
splice(start, [deleteCount])
splice(start, [deleteCount], [item1])
splice(start, [deleteCount], [item1], [item2], [itemN])
```

- **Parameters:**
  - `start`
    - The index at which to start changing the array.
    - If *greater than the length of the array*, start will be set to the length of the array. In this case, no element will be deleted but the method will *behave as an adding function*, adding as many element as item[n*] provided.

      ```js
      const months = ['Jan', 'March', 'April', 'June'];
      console.log(months.length) //4
      months.splice(10, 0, 'test')
      console.log(months) //["Jan", "March", "April", "June", "test"]
      console.log(months.length) //5
      ```

    - If *negative*, it will begin that many elements from the *end of the array*. (In this case, the origin -1, meaning -n is the index of the nth last element, and is therefore equivalent to the index of array.length - n.) If start is negative infinity, it will begin from index 0.
  
      ```js
      const months = ['Jan', 'March', 'April', 'June'];
      months.splice(-1, 0, 'test')
      console.log(months) //["Jan", "March", "April", "test", "June"]
      ```

  - `[deleteCount]`
    - An integer indicating the number of elements in the array to remove from `start`.
    - If deleteCount is *omitted*, or if its *value is equal to or larger than `array.length - start`* (that is, if it is equal to or greater than the number of elements left in the array, starting at start), ***then all the elements from start to the end of the array will be deleted.***
    - If deleteCount is* 0 or negative*, no elements are removed. In this case, you should specify at least one new element (see below).
  - `[item1, item2, ... ]`
    - The elements to add to the array, beginning from start. If you do not specify any elements, `splice()` will only remove elements from the array.

- **Return Value:**
  - An array containing the deleted elements.
  - If only one element is removed, an array of one element is returned.
  - If no elements are removed, an empty array is returned.

#### `.slice()` - method [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

Returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array. *The original array will not be modified.*

- **Syntax:** `slice([start], [end])`
- **Parameters:**
  - `[start]`
    - Zero-based index at which to start extraction.
    - A negative index can be used, indicating an *offset from the end of the sequence*. slice(-2) extracts the last two elements in the sequence.
    - If start is undefined, slice starts from the index 0.
    - If start is greater than the index range of the sequence, an empty array is returned.
  - `[end]`
    - Zero-based index before which to end extraction. `slice` extracts up to *but not including end*. For example, slice(1,4) extracts the second element through the fourth element (elements indexed 1, 2, and 3).
    - A negative index can be used, *indicating an offset from the end of the sequence*. slice(2,-1) extracts the third element through the second-to-last element in the sequence.
    - If `end` is omitted, `slice` extracts through the end of the sequence `(arr.length)`.
    - If `end` is greater than the length of the sequence, slice extracts through to the end of the sequence `(arr.length)`.

- **Return Value:** A new array containing the extracted elements.

## `console.`

### `.log()`

`console.log({var})` - prints the variable name and the value it holds

### `.table()`

[dmo](https://developer.mozilla.org/en-US/docs/Web/API/console/table)

- method displays tabular data as a table.
- This function takes one mandatory argument data, which must be an `array` or an `object`, and one additional optional parameter `columns` is the name of columns to print for objects

**syntax**:

```js
console.table(data);
console.table(data, columns);
```

## `RegExp` - object [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp)

used for matching text with a pattern.

There are two ways to create a RegExp object: 
- **The literal notation's** parameters are enclosed between slashes and do not use quotation marks.
- **The constructor function's** parameters are not enclosed between slashes but do use quotation marks.

```js
let re = /ab+c/i; // literal notation
let re = new RegExp('ab+c', 'i') // constructor with string pattern as first argument
let re = new RegExp(/ab+c/, 'i') // constructor with regular expression literal as first argument (Starting with ECMAScript 6)
```

### constructor [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp/RegExp)

creates a regular expression object for matching text with a pattern. 

## `String`

### `.prototype` (string)

#### `.replace()` - method [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace)

#### `.includes()` [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)

- method performs a case-sensitive search to determine whether one string may be found within another string, returning `true` or `false` as appropriate.

**Syntax**: `replace(regexp || substr, newSubstr || replacerFunction)`

**Parameters:**
- `regexp` (pattern)
  - A `RegExp` object or literal.
  - The match or matches are replaced with `newSubstr` or the value returned by the specified `replacerFunction`.
- `substr`
  - A `String` that is to be replaced by `newSubstr`.
  - It is treated as a literal string and is not interpreted as a regular expression. 
  - Only the first occurrence will be replaced.
- `newSubstr` (replacement)
  - The `String` that replaces the substring specified by the specified `regexp` or `substr` parameter. 
  - A number of special replacement patterns are supported; see the "[Specifying a string as a parameter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace#specifying_a_string_as_a_parameter)"
  - If `newSubstr` is an empty string, then the substring given by `substr`, or the matches for `regexp`, are *****removed***** (rather then being replaced).
- `replacerFunction` (replacement)
  - A function to be invoked to create the new substring to be used to replace the matches to the given `regexp` or `substr`.
  The arguments supplied to this function are described in the "[Specifying a function as a parameter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace#specifying_a_function_as_a_parameter)"

**Return value** - A new string, with some or all matches of a pattern replaced by a replacement.


**Syntax**:

```js
includes(searchString)
includes(searchString, position) //position where to start the search
```

### `.match()` - method [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match)

- sreaches a string based on a regex and retruns found string
- **Syntax:** `match(regexp)`
- **Parameters:**
  - `regexp` regular expression object
    - if it isnt a `RegExp` object it will be converted
    - it is left empty `[""]` is returned
- **Return Value:**
  - `null` - no matches are found
  - `Array` - of found matches
    - if `g` flag is used in the regex
      - all matching results are returned
      - capturing groups are not returned
    - if `g` flag is not used
      - only first match is returned
      - the first match's related capturing groups are also returned
      - it will have additional properties
        - `groups`
          - object of named capturing groups
          - [!!todo look up groups and ranges!!](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions/Groups_and_Ranges)
        - `index`
          - the index of the search at which the result was found
          - `input` a copy of the search string
- consider other methods if `g` flag is not being used
  - `RegExp.test()` - returns just a boolean
  - `RegExp.exec()` - just want the first result
  - `RegExp.exec()` or `String.prototype.matchAll()` - to get capture groups with the global flag is on

## fetch() [dmo](https://developer.mozilla.org/en-US/docs/Web/API/fetch)

- global method starts the process of fetching a resource from the network, returning a promise which is fulfilled once the response is available.
- **Syntax:** `const fetchResponsePromise = fetch(resource [, init])`
- **Parameters:**
  - `resource` - can be either
    - stirng: the url request to fetch
    - `Request` object
  - `[init]` object
    - contains any custom settingsfor the request
    - options included
      - `method` - eg GET, POST
      - `headers` 
      - ... a whole bunch of stuff that is needed for making calls
- **Returns:** `Promise` that resolves to a `Response` object.
- Since it returns a promise it be followed up by [promise methods](#promisedmo)

## Promise [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

### `.then()` [dmo](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then)

- **Syntax:** 
  ```js
  p.then(onFulfilled[, onRejected]);

  p.then(value => {
    // fulfillment
  }, reason => {
    // rejection
  });
  ```
- **Parameters:**
  - `[onFulfilled]` *function*
    - if the preceding promise is fulfilled it will call this function
    - variables passed to it:
      - `value` - what the preceding promise returns on successfully completion
  - `[onRejected]`  *function*
    - if the preceding promise is rejected this function will be called
    - variables passed to it:
      - `reason` - the rejection reason
- **Returns:** it depends on the onFulfilled and onRejected functions used:
  - return a value:
    - the promise returned by `then` gets resolved with the returned value as its value.
  - nothing is returned
    - the promise returned by `then` gets resolved with an `undefined` value.
  - error thrown
    - the promise returned by `then` gets rejected with the thrown error as its value.
  - returns an already fulfilled promise
    - the promise returned by `then` gets fulfilled with that promise's value as its value.
  - returns an already rejected promise
    - the promise returned by `then` gets rejected with that promise's value as its value.
  - returns another pending promise object
    - the resolution/rejection of the promise returned by `then` will be subsequent to the resolution/rejection of the promise returned by the handler
    - the resolved value of the promise returned by `then` will be the same as the resolved value of the promise returned by the handler.

## Response - Interface [dmo](https://developer.mozilla.org/en-US/docs/Web/API/Response)

### `.json()` - method [dmo](https://developer.mozilla.org/en-US/docs/Web/API/Response/json)

- takes a `Response` stream and reads it to completion. It returns a promise which resolves with the result of parsing the body text as `JSON`.
- **Syntax:** `response.json()`
- **Parameters:** - nothing
- **Returns:** - a [promise](#promisedmo) that resolves to a JavaScript object. This object could be anything that can be represented by JSON — an object, an array, a string, a number...


