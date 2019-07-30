# Introduction to the Functional Programming Challenges

Functional programming is an approach to software development based around the evaluation of functions. Like mathematics, functions in programming map input to output to produce a result. You can combine basic functions in many ways to build more and more complex programs.

Functional programming follows a few core principles:



- Functions are independent from the state of the program or global variables. They only depend on the arguments passed into them to make a calculation
- Functions try to limit any changes to the state of the program and avoid changes to the global objects holding data
- Functions have minimal side effects in the program



The functional programming software development approach breaks a program into small, testable parts. This section covers basic functional programming principles in JavaScript.

<br>

<br>

### Learn About Functional Programming

Functional programming is a style of programming where solutions are simple, isolated functions, without any side effects outside of the function scope.

```pseudocode
INPUT -> PROCESS -> OUTPUT
```

Functional programming is about:

1) Isolated functions - there is no dependence on the state of the program, which includes global variables that are subject to change

2) Pure functions - the same input always gives the same output

3) Functions with limited side effects - any changes, or mutations, to the state of the program outside the function are carefully controlled

```javascript
/**
 * A long process to prepare tea.
 * @return {string} A cup of tea.
 **/
const prepareTea = () => 'greenTea';

/**
 * Get given number of cups of tea.
 * @param {number} numOfCups Number of required cups of tea.
 * @return {Array<string>} Given amount of tea cups.
 **/
const getTea = (numOfCups) => {
  const teaCups = [];
  
  for(let cups = 1; cups <= numOfCups; cups += 1) {
    const teaCup = prepareTea();
    teaCups.push(teaCup);
  }

  return teaCups;
};

// Add your code below this line

const tea4TeamFCC = getTea(40); // :(

// Add your code above this line

console.log(tea4TeamFCC);
```

<br>

### Understand Functional Programming Terminology

