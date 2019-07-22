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

Return the provided string with the first letter of each word capitalized. Make sure the rest of the word is in lower case.

For the purpose of this exercise, you should also capitalize connecting words like "the" and "of".

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function titleCase(str) {
    let wordContainer = str.split(' ');
    let copiedStr = [];
    for(let i = 0; i < wordContainer.length; i++){
        for(let j = 0; j < wordContainer[i].length; j++){
            // console.log(wordContainer[i]);
            if(j==0){
                copiedStr.push(wordContainer[i][j].toUpperCase());
            }else{
                copiedStr.push(wordContainer[i][j].toLowerCase());
            }
        }
        copiedStr.push(' ');
    }
    copiedStr.pop();
    wordContainer = copiedStr.join('');
    console.log(wordContainer);
    return wordContainer;
}

titleCase("I'm a little tea pot");
```

<br>

### Slice and Splice

You are given two arrays and an index.

Use the array methods `slice`and `splice`to copy each element of the first array into the second array, in order.

Begin inserting elements at index `n`of the second array.

Return the resulting array. The input arrays should remain the same after the function runs.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function frankenSplice(arr1, arr2, n) {
    // It's alive. It's alive!
    let arr3 = [];

    for(let i=0; i < n; i++){
        arr3.push(arr2[i]);
    }
    let arr4 = (arr2.slice(n, arr2.length));
    for(let i = 0; i < arr1.length; i++){
        arr3.push(arr1[i]);
    }
    for(let i =0;i < arr4.length;i++){
        arr3.push(arr4[i]);
    }
    return arr3;
}

frankenSplice([1, 2, 3], [4, 5, 6], 1);
```

```javascript
function frankenSplice(arr1, arr2, n) {
    // It's alive. It's alive!
    let localArray = arr2.slice();
    for (let i = 0; i < arr1.length; i++) {
        localArray.splice(n, 0, arr1[i]);
        n++;
    }
    return localArray;
}
```

<br>

### Falsy Bouncer

Remove all falsy values from an array.

Falsy values in JavaScript are `false`, `null`, `0`, `""`, `undefined`, and `NaN`.

Hint: Try converting each value to a Boolean.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function bouncer(arr) {
    // Don't show a false ID to this bouncer.
    let newArr = arr.filter((ele)=>{
        if(ele){
            return ele;
        }
    })
    console.log(newArr);
    return newArr;
}

bouncer([1, null, NaN, 2, undefined]);
// filter() method는 원 배열을 변형시키지 않는다.
```

```javascript
function bouncer(arr) {
    return arr.filter(Boolean);
}
```

<br>

### Where do I Belong

Return the lowest index at which a value (second argument) should be inserted into an array (first argument) once it has been sorted. The returned value should be a number.

For example, `getIndexToIns([1,2,3,4], 1.5)`should return `1`because it is greater than `1`(index 0), but less than `2`(index 1).

Likewise, `getIndexToIns([20,3,5], 19)`should return `2`because once the array has been sorted it will look like `[3,5,20]`and `19`is less than `20`(index 2) and greater than `5`(index 1).

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function CompareForSort(first, second)
{
    if (first == second)
        return 0;
    if (first < second)
        return -1;
    else
        return 1; 
}

function getIndexToIns(arr, num) {
    // Find my place in this sorted array.
    arr.sort(CompareForSort);
    console.log(arr);
    let putIndex = 0;
    for(let i = 0; i < arr.length; i++){
        if(num == arr[i]){
            putIndex = i;
        }else if(num > arr[i]){
            putIndex = i+1;
        }
    }
    return putIndex;
}
console.log(getIndexToIns([5, 3, 20, 3], 5));
getIndexToIns([5, 3, 20, 3], 5);
```

<br>

### Mutations

Return true if the string in the first element of the array contains all of the letters of the string in the second element of the array.

For example, `["hello", "Hello"]`, should return true because all of the letters in the second string are present in the first, ignoring case.

The arguments `["hello", "hey"]`should return false because the string "hello" does not contain a "y".

Lastly, `["Alien", "line"]`, should return true because all of the letters in "line" are present in "Alien".

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function mutation(arr) {
    arr[0] = arr[0].toLowerCase();
    arr[1] = arr[1].toLowerCase();
    console.log(arr[1].split(''));
    let checkedValue = true;
    for(let i = 0; i < arr[1].length; i++){
        if(arr[0].indexOf(arr[1][i]) === -1){
            checkedValue = false;
            return checkedValue;
        }
    }

    return checkedValue;
}

mutation(["hello", "Hey"]);
```

<br>

### Chunky Monkey

Write a function that splits an array (first argument) into groups the length of `size`(second argument) and returns them as a two-dimensional array.

Remember to use [Read-Search-Ask](http://forum.freecodecamp.org/t/how-to-get-help-when-you-are-stuck/19514) if you get stuck. Write your own code.

```javascript
function chunkArrayInGroups(arr, size) {
    // Break it up.
    let wholeArr = [];
    let countNum = Math.ceil(arr.length/size);
    console.log(countNum);
    for(let i = 0; i < countNum; i++){
        let nestArr = [];
        nestArr = arr.slice(size*i, size*(i+1))
        wholeArr.push(nestArr);
    }
    console.log(wholeArr);
    return wholeArr;
}

chunkArrayInGroups([0, 1, 2, 3, 4, 5], 4);
```

```javascript
function chunkArrayInGroups(arr, size) {
    // Break it up.
    var newArr = [];
    var i = 0;

    while (i < arr.length) {
        newArr.push(arr.slice(i, i+size));
        i += size;
    }
    return newArr;
}
chunkArrayInGroups(["a", "b", "c", "d"], 2);
```

