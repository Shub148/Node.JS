# Node.js - Importing & Exporting Modules

## What is `require()`?

`require()` is used to import a module (file) into another file.

If both files are in the same folder, use:

```javascript
const math = require("./math");
```

- `./` means the current directory.
- Node.js automatically looks for `math.js`.

---

# Exporting Data from Another File

Suppose we have a file named `math.js`.

```javascript
const sum = (a, b) => a + b;
const mul = (a, b) => a * b;
const g = 9.8;
const PI = 3.14;

module.exports = {
    sum,
    mul,
    g,
    PI,
};
```

Import it into another file:

```javascript
const math = require("./math");

console.log(math.sum(2, 2));
console.log(math.mul(2, 3));
console.log(math.PI);
console.log(math.g);
```

Output:

```
4
6
3.14
9.8
```

---

# Different Ways to Export

## 1. Export an Object (Most Common)

```javascript
module.exports = {
    sum,
    mul,
    PI,
    g,
};
```

---

## 2. Export a Single Value

```javascript
module.exports = sum;
```

Import:

```javascript
const sum = require("./math");

console.log(sum(2, 3));
```

---

## 3. Using `exports`

```javascript
exports.sum = (a, b) => a + b;
exports.mul = (a, b) => a * b;
exports.PI = 3.14;
exports.g = 9.8;
```

Import:

```javascript
const math = require("./math");

console.log(math.sum(5, 5));
```

> **Note:** Do not write:

```javascript
exports sum = ...
```

Correct syntax:

```javascript
exports.sum = ...
```

---

# Exporting Objects

### apple.js

```javascript
module.exports = {
    name: "apple",
    color: "red",
};
```

### banana.js

```javascript
module.exports = {
    name: "banana",
    color: "yellow",
};
```

### mango.js

```javascript
module.exports = {
    name: "mango",
    color: "yellow",
};
```

---

# Import Multiple Files

Create an `index.js` inside the `fruit` folder.

```javascript
const apple = require("./apple");
const banana = require("./banana");
const mango = require("./mango");

let fruits = [apple, banana, mango];

module.exports = fruits;
```

Now import the entire folder.

```javascript
const fruits = require("./fruit");

console.log(fruits);
console.log(fruits[0]);
console.log(fruits[0].name);
```

Output:

```
[
  { name: 'apple', color: 'red' },
  { name: 'banana', color: 'yellow' },
  { name: 'mango', color: 'yellow' }
]

{ name: 'apple', color: 'red' }

apple
```

---

# Folder Structure

```
backend/
│
├── script.js
├── math.js
│
└── fruit/
    ├── index.js
    ├── apple.js
    ├── banana.js
    └── mango.js
```

---

# Important Notes

✅ `module.exports` exports data from a file.

✅ `require()` imports data into another file.

✅ `./` refers to the current directory.

✅ `index.js` is loaded automatically when requiring a folder.

Example:

```javascript
const fruits = require("./fruit");
```

Node.js automatically loads:

```
fruit/index.js
```

---

# Common Errors

### ❌ Invalid shorthand property initializer

Wrong:

```javascript
module.exports = {
    name = "apple",
};
```

Correct:

```javascript
module.exports = {
    name: "apple",
};
```

---

### ❌ `math.sum is not a function`

Possible reasons:

- You exported only one value instead of an object.
- You forgot to save the file.
- `module.exports` was overwritten.

Correct:

```javascript
module.exports = {
    sum,
    mul,
    PI,
    g,
};
```

---

# Summary

- `require()` → Import modules.
- `module.exports` → Export modules.
- `exports` → Shortcut for exporting multiple properties.
- `index.js` → Default file loaded when importing a folder.
- Organize related files into folders and export them through `index.js`.
