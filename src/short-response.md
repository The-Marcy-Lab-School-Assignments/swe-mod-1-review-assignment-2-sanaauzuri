# Short Responses

For this short response assignment, aim to write a response with the following qualities (your instructor will give you feedback on these areas):
- [] Addresses all parts of the prompt
- [] Accurately uses relevant technical terminology
- [] Is free of grammar and spelling mistakes (double check with grammarly!)
- [] Uses markdown to enhance readability (preview in VS Code with Command/Control + Shift + V)
- [] Is easy to comprehend

For each prompt below, write your response in the space provided. Aim to answer each prompt in 2-5 concise sentences. Make sure to preview your markdown to check how it is rendered before submitting.

## Prompt 1

Read the following code:

```js
const playlist1 = { name: "My Favorites", songCount: 10 };
const playlist2 = playlist1;
playlist2.songCount = 15;
console.log(playlist1.songCount);
```

Part A: What will be logged to the console? Why?

Part B: How would you modify the code so that reassigning `playlist2.songCount` does NOT affect `playlist1`.songCount? Write the corrected code below your response (we've provided the broken code again for you to fix).

### Response 1
`A)`  What will be logged to the console:
```javascript
{ name: "My Favorites", songCount: 15 };
```
Explanation: This is logged to the console because both variables point to the same object, so mutating the object through one variable means that mutation is reflected through the other variable too.

`B)` I would modify the code by using spread syntax to create a copy of the original object, so that reassigning `playlist2.songCount` does NOT affect `playlist1`.songCount

**Corrected Code:**
```js
// fix this!
const playlist1 = { name: "My Favorites", songCount: 10 };
const playlist2 = { ...playlist1 };
playlist2.songCount = 15;
console.log(playlist1.songCount);
```

---

## Prompt 2

```js
const students = [
  { name: "Maya", grade: 92, passed: true },
  { name: "Jamal", grade: 78, passed: true },
  { name: "Destiny", grade: 88, passed: true },
  { name: "Marcus", grade: 95, passed: true }
];
```

For each task below, identify which array method (forEach, filter, map, find, or reduce) you would use.

1. You need to get an array containing only students who scored above 85.
2. You need to find the student named "Destiny" and update their grade to 90.
3. You need to calculate the average grade of all students.
4. You need to create an array of strings in the format: "Maya: 92"

### Response 2

1. Array method: `Array.filter()`.
2. Array method: `Array.find()`.
3. Array method: `Array.reduce()`.
4. Array method: `Array.map()`.


## Prompt 3

We should expect that the code below prints the array `[ 'A', 'B', 'C', 'D' ]` but an error is thrown when the third line of code is executed.

Explain why this error occurs, how to fix it, and provide a suggestion for how to avoid this error in the future.

```js
const letters = ['a', 'b', 'c', 'd'];
const capitalize = (str) => str.toUpperCase();

const upperCaseLetters = letters.map(capitalize());
// Uncaught TypeError: Cannot read properties of undefined (reading 'toUpperCase')

console.log(upperCaseLetters);
```

### Response 3

Why the error occurs:


This error occurs because the `.map()` doesn't receive a callback function. `capitalize()` is called with no argument, so `str` is `undefined` and the function returns `undefined`. `.map()` gets undefined where it expects a callback function.  So when it tries to call it on each element, it throws an error because the callback function is placed where the element being processed in the array method should be.


Fix:

Remove empty parentheses so the function itself is passed, not called immediately.

To avoid in the future:

You can avoid this error by either storing the callback function inside the array method instead of a variable or not including parentheses when passing a function as a callback in an array method.

## Prompt 4

Given this code:

```js
const orders = [
  { id: 1, total: 45 },
  { id: 2, total: 23 },
  { id: 3, total: 67 }
];

const grandTotal = orders.reduce((sum, order) => {
  return sum + order.total;
}, 0);
```

- Part A: What will `grandTotal` equal after this code runs?
- Part B: Explain what the `0` at the end of the reduce method does. Why is it important?
- Part C: Walk through what happens in the FIRST iteration of reduce:
    - What is the value of sum?
    - What is the value of order?
    - What gets returned?

### Response 4

- Part A: The grand total will equal 135 after this code runs.
- Part B: The 0 at the end of the `reduce method` sets the initial value for the callback function. Without an initial value, the sum would start at the first element of the array. The `initial value` prevents this by giving the `accumulator` a correct starting point.
- Part C: Walk through what happens in the FIRST iteration of reduce:
   - The value of sum is 0 (the `initial value`)
   - The value of order is `{ id: 1, total: 45 }`, the first object in the array
   - The sum, which is 0, added onto the value of `order.total` for the first iteration gets returned. For example:
   `Iteration 1:` 0 + 45 is returned, so sum becomes 45 going into the next iteration


