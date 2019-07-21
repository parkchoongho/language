# Introduction to Basic Algorithm Scripting

A computer algorithm is a sequence of steps that is followed to achieve a particular outcome. To write an algorithm, you must first understand a problem, and then solve it with coding.

To make solving problems easier, it can be helpful to break them down into many chunks. Then, each chunk can be solved one by one. For example, if you are building a calculator, don't try to solve the problem as a whole. First, consider how to get inputs. Then, determine each arithmetic operation one by one. Finally, display the results.

In this section we will learn to solve basic algorithm problems using JavaScript. This will help you improve your problem solving skills and prepare you to later solve more complex problems.

#### Hint

If you get stuck, try using `console.log()`to log variable values to the console. This will help to debug problems.

<br>

<br>

### Convert Celsius to Fahrenheit

The algorithm to convert from Celsius to Fahrenheit is the temperature in Celsius times `9/5`, plus `32`.

You are given a variable `celsius`representing a temperature in Celsius. Use the variable `fahrenheit`already defined and assign it the Fahrenheit temperature equivalent to the given Celsius temperature. Use the algorithm mentioned above to help convert the Celsius temperature to Fahrenheit.

Don't worry too much about the function and return statements as they will be covered in future challenges. For now, only use operators that you have already learned.

```javascript
function convertToF(celsius) {
    let fahrenheit;
    fahrenheit = celsius*9/5+32;
    return fahrenheit;
}

convertToF(30);
```

<br>

### Reverse a String

Reverse the provided string.

You may need to turn the string into an array before you can reverse it.

Your result must be a string.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function reverseString(str) {
    let copiedStr = [];

    for(let i = str.length-1; i >= 0; i--){
        copiedStr.push(str[i]);
    }
    str = copiedStr.join('');

    return str;
}

reverseString("hello");
```

<br>

### Factorialize a Number

Return the factorial of the provided integer.

If the integer is represented with the letter n, a factorial is the product of all positive integers less than or equal to n.

Factorials are often represented with the shorthand notation `n!`

For example: `5! = 1 * 2 * 3 * 4 * 5 = 120`

Only integers greater than or equal to zero will be supplied to the function.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function factorialize(num) {
  let mul = 1;
  
  for(let i = num; i >= 1; i--){
    mul *= i;
  }

  return mul;
}

console.log(factorialize(5));
```

```javascript
function factorialize(num) {
  if(num==0){
    return 1;
  }
  return num*factorialize(num-1)
}

console.log(factorialize(5));
```

<br>

### Find the Longest Word in a String

Return the length of the longest word in the provided sentence.

Your response should be a number.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function findLongestWordLength(str) {
    let wordContainer = str.split(' '); 
    console.log(wordContainer);
    let max = wordContainer[0].length;
    for(let i = 1; i < wordContainer.length; i++){
        if(wordContainer[i].length > max){
            max = wordContainer[i].length
        }
    } 
    return max;
}

findLongestWordLength("The quick brown fox jumped over the lazy dog");
```

<br>

### Return Largest Numbers in Arrays

Return an array consisting of the largest number from each provided sub-array. For simplicity, the provided array will contain exactly 4 sub-arrays.

Remember, you can iterate through an array with a simple for loop, and access each member with array syntax `arr[i]`.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function largestOfFour(arr) {
    // You can do this!
    let newArr = [];
    let max;
    for(let i = 0; i < arr.length; i++){
        max = arr[i][0];
        for(let j = 1; j < arr[i].length; j++){
            if(arr[i][j] > max){
                max = arr[i][j];
            }
        }
        console.log(max);
        newArr.push(max);
    }
    return newArr;
}

largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]);
```

<br>

### Confirm the Ending

Check if a string (first argument, `str`) ends with the given target string (second argument, `target`).

This challenge *can* be solved with the `.endsWith()`method, which was introduced in ES2015. But for the purpose of this challenge, we would like you to use one of the JavaScript substring methods instead.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function confirmEnding(str, target) {
    // "Never give up and good luck will find you."
    // -- Falcor
    let wordContainer = str.split(' ');
    let checkedValue = true;
    let checkedString = wordContainer[wordContainer.length - 1];
    console.log(wordContainer);
    console.log(checkedString);


    for(let i = 0; i < target.length; i++){
        if(target[target.length -1 -i] != checkedString[checkedString.length -1 -i]){
            console.log(target[target.length -1 -i]);
            console.log(checkedString[checkedString.length -1 -i]);
            checkedValue = false;
            return checkedValue;
        }
    }
    return checkedValue;
}

confirmEnding("Open Connor", "n");
```

```javascript
function confirmEnding(str, target) {
    // "Never give up and good luck will find you."
    // -- Falcor
    return str.slice(str.length - target.length) === target;
}

confirmEnding("Open Connor", "n");
```

<br>

### Repeat a String Repeat a String

Repeat a given string `str`(first argument) for `num`times (second argument). Return an empty string if `num`is not a positive number.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function repeatStringNumTimes(str, num) {
    // repeat after me
    let attachStr= "";
    if(num > 0){
        for(let i = 0; i < num; i++){
            attachStr += str;
        }
    }
    console.log(attachStr);
    return attachStr;
}

repeatStringNumTimes("abc", 3);
```

```javascript
function repeatStringNumTimes(str, num) {
    if(num < 0)
        return "";
    if(num === 1)
        return str;
    else
        return str + repeatStringNumTimes(str, num - 1);
}
```

<br>

### Truncate a String

Truncate a string (first argument) if it is longer than the given maximum string length (second argument). Return the truncated string with a `...`ending.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function truncateString(str, num) {
    // Clear out that junk in your trunk
    let appliStr = str.slice(0, num);

    if(str.length > num){
        appliStr += '...';
    }

    console.log(appliStr);
    return appliStr;
}

truncateString("A-tisket a-tasket A green and yellow basket", 8);
```

<br>

### Finders Keepers

Create a function that looks through an array (first argument) and returns the first element in the array that passes a truth test (second argument). If no element passes the test, return undefined.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Try to pair program. Write your own code.

```javascript
function findElement(arr, func) {
    for(let i=0; i < arr.length; i++){
        if(func(arr[i])){
            return arr[i];
        }
    }
    return undefined;
}

findElement([1, 2, 3, 4], num => num % 2 === 0);
```

<br>

### Boo who

Check if a value is classified as a boolean primitive. Return true or false.

Boolean primitives are true and false.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Try to pair program. Write your own code.

```javascript
function booWho(bool) {
    // What is the new fad diet for ghost developers? The Boolean.
    if(bool===true||bool===false){
        return true;
    }else{
        return false;
    }
}

booWho(null);
```

```javascript
function booWho(bool) {
    return typeof bool === 'boolean';
}

// test here
booWho(null);
```

<br>

### Title Case a Sentence