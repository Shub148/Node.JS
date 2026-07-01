# Node.JS

 ---

# Complete Code Reference

## 1. math.js

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

---

## 2. script.js (Using math.js)

```javascript
const math = require("./math");

console.log(math);

console.log(math.sum(2, 2));
console.log(math.mul(2, 2));
console.log(math.PI);
console.log(math.g);
```

Output

```
{
  sum: [Function: sum],
  mul: [Function: mul],
  g: 9.8,
  PI: 3.14
}

4
4
3.14
9.8
```

---

## 3. apple.js

```javascript
module.exports = {
    name: "apple",
    color: "red",
};
```

---

## 4. banana.js

```javascript
module.exports = {
    name: "banana",
    color: "yellow",
};
```

---

## 5. mango.js

```javascript
module.exports = {
    name: "mango",
    color: "yellow",
};
```

---

## 6. fruit/index.js

```javascript
const apple = require("./apple");
const banana = require("./banana");
const mango = require("./mango");

let fruits = [apple, banana, mango];

module.exports = fruits;
```

---

## 7. script.js (Using fruit Folder)

```javascript
const fruits = require("./fruit");

console.log(fruits);

console.log(fruits[0]);

console.log(fruits[0].name);

console.log(fruits[1].name);

console.log(fruits[2].name);
```

Output

```
[
  { name: 'apple', color: 'red' },
  { name: 'banana', color: 'yellow' },
  { name: 'mango', color: 'yellow' }
]

{ name: 'apple', color: 'red' }

apple
banana
mango
```

---

# Project Structure

```
backend/
│
├── script.js
├── math.js
│
└── fruit/
    ├── apple.js
    ├── banana.js
    ├── mango.js
    └── index.js
```

---

# Key Takeaways

- `require()` imports a module.
- `module.exports` exports data from a file.
- `exports` is a shortcut for `module.exports.property`.
- `./` represents the current directory.
- `index.js` is automatically loaded when a folder is required.
- A folder can act as a module by exporting its data through `index.js`.

---

## Practice Questions

1. Create a `calculator.js` module with `add()`, `subtract()`, `multiply()`, and `divide()` functions.
2. Import the module into `script.js` and perform different operations.
3. Create a `vehicles` folder containing `car.js`, `bike.js`, and `bus.js`.
4. Export all vehicle objects using `vehicles/index.js`.
5. Import the `vehicles` folder and print the details of each vehicle.
6. Create a `students` folder with three student files and export them as an array using `index.js`.
7. Try exporting a single function instead of an object and import it into another file.

---

**End of Notes**
