

# JavaScript Utility Functions 🛠️

A collection of essential JavaScript utility functions for everyday development tasks. This repository contains reusable functions to enhance productivity, improve code readability, and optimize web performance. Each function includes usage examples and explanations, making it easy to integrate them into your projects.

## 🔍 Table of Contents
1. [Debounce Function](#1-debounce-function)
2. [Deep Clone an Object](#2-deep-clone-an-object)
3. [Capitalize Each Word in a String](#3-capitalize-each-word-in-a-string)
4. [Random Integer Generator](#4-random-integer-generator)
5. [Flatten an Array](#5-flatten-an-array)
6. [Check if a String is a Palindrome](#6-check-if-a-string-is-a-palindrome)
7. [Get Query Parameters from a URL](#7-get-query-parameters-from-a-url)
8. [Generate a UUID](#8-generate-a-uuid)
9. [Sort an Array of Objects by Key](#9-sort-an-array-of-objects-by-key)
10. [Convert RGB to Hex Color](#10-convert-rgb-to-hex-color)

## ⚙️ Functions

### 1. Debounce Function
Limits the rate at which a function can fire. Useful for event handling such as resizing or scrolling.

```javascript
function debounce(func, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => func.apply(this, args), delay);
  };
}
```

**Usage:**
```javascript
window.addEventListener('resize', debounce(() => {
  console.log('Resize event');
}, 500));
```

---

### 2. Deep Clone an Object
Creates a deep copy of an object, preserving nested structures.

```javascript
function deepClone(obj) {
  return JSON.parse(JSON.stringify(obj));
}
```

**Usage:**
```javascript
const original = { name: 'Alice', skills: ['JS', 'CSS'] };
const clone = deepClone(original);
console.log(clone);
```

---

### 3. Capitalize Each Word in a String
Capitalizes the first letter of each word in a string.

```javascript
function capitalizeWords(str) {
  return str.replace(/\b\w/g, char => char.toUpperCase());
}
```

**Usage:**
```javascript
console.log(capitalizeWords('hello world')); // "Hello World"
```

---

### 4. Random Integer Generator
Generates a random integer between two specified values.

```javascript
function getRandomInt(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
```

**Usage:**
```javascript
console.log(getRandomInt(1, 100));
```

---

### 5. Flatten an Array
Flattens a nested array into a single-level array.

```javascript
function flattenArray(arr) {
  return arr.reduce((flat, toFlatten) =>
    flat.concat(Array.isArray(toFlatten) ? flattenArray(toFlatten) : toFlatten), []);
}
```

**Usage:**
```javascript
console.log(flattenArray([1, [2, [3, 4], 5]])); // [1, 2, 3, 4, 5]
```

---

### 6. Check if a String is a Palindrome
Verifies if a string is the same when read forwards and backwards.

```javascript
function isPalindrome(str) {
  const sanitizedStr = str.toLowerCase().replace(/[^a-z0-9]/g, '');
  return sanitizedStr === sanitizedStr.split('').reverse().join('');
}
```

**Usage:**
```javascript
console.log(isPalindrome('A man, a plan, a canal, Panama')); // true
```

---

### 7. Get Query Parameters from a URL
Extracts query parameters from a URL as an object.

```javascript
function getQueryParams(url) {
  const params = new URLSearchParams(url.split('?')[1]);
  return Object.fromEntries(params.entries());
}
```

**Usage:**
```javascript
console.log(getQueryParams('http://example.com/?name=John&age=30')); // { name: 'John', age: '30' }
```

---

### 8. Generate a UUID
Generates a universally unique identifier (UUID).

```javascript
function generateUUID() {
  return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function(c) {
    const r = Math.random() * 16 | 0, v = c === 'x' ? r : (r & 0x3 | 0x8);
    return v.toString(16);
  });
}
```

**Usage:**
```javascript
console.log(generateUUID());
```

---

### 9. Sort an Array of Objects by Key
Sorts an array of objects based on a specified key.

```javascript
function sortByKey(arr, key) {
  return arr.sort((a, b) => (a[key] > b[key] ? 1 : -1));
}
```

**Usage:**
```javascript
const data = [{name: 'John', age: 30}, {name: 'Alice', age: 25}];
console.log(sortByKey(data, 'age'));
```

---

### 10. Convert RGB to Hex Color
Converts RGB values to a hexadecimal color code.

```javascript
function rgbToHex(r, g, b) {
  return `#${((1 << 24) | (r << 16) | (g << 8) | b).toString(16).slice(1).toUpperCase()}`;
}
```

**Usage:**
```javascript
console.log(rgbToHex(255, 99, 71)); // "#FF6347"
```



