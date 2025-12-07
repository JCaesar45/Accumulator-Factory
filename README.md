```markdown
# Accumulator Factory in JavaScript

## Overview
This project implements an **Accumulator Factory** in JavaScript, inspired by a problem posed by Paul Graham. It creates a function that generates accumulator functions, which maintain a running total of all numbers passed to them over time.

## What it does
- You provide an initial number `n` to create an accumulator.
- The returned accumulator is a function that:
  - Takes a single numeric argument.
  - Adds this number to the total sum maintained internally.
  - Returns the current total sum.

## Usage

### Creating an accumulator
```javascript
const accumulator = createAccumulator(0); // start with 0
```

### Using the accumulator
```javascript
console.log(accumulator(2)); // Output: 2
console.log(accumulator(3)); // Output: 5
console.log(accumulator(-1)); // Output: 4
``

### Multiple accumulators
You can create multiple independent accumulators:
```javascript
const acc1 = createAccumulator(10);
const acc2 = createAccumulator(100);

console.log(acc1(5)); // Output: 15
console.log(acc2(50)); // Output: 150
``

## How it works
- The core function `createAccumulator(n)` initializes a local variable `total` with the starting value `n`.
- It returns an inner function that:
  - Adds the argument to `total`.
  - Returns `total`.
- Thanks to closures, each accumulator maintains its own independent `total`.

## Code
```javascript
function createAccumulator(n) {
  let total = n;
  return function (num) {
    total += num;
    return total;
  };
}
``

## Rules & Notes
- No global variables are used.
- The accumulator functions maintain their own internal state via closures.
- Designed for numeric inputs only.

## License
This is a simple utility function for educational purposes.
