# Basic JavaScript

### Declare JavaScript Variables

**JavaScript는 기본적으로 7개의 서로 다른 type의 data를 제공한다.**

`undefined`, `null`, `boolean`, `string`, `symbol`, `number`, `object`

변수는 컴퓨터가 동적인 방식으로 데이터를 저장하고 조작할 수 있게 도와주는 역할을 한다. 변수들은 이것을 **데이터 그 자체를 이용해서 하기 보다는 "label"을 활용해 데이터를 가리키는 방식**으로 이를 가능케 한다. 

```javascript
var ourName;
```

 `ourName` 이라 불리는  `variable`을 선언한 것이다. `Variable`은 숫자나 문자 그리고 `$` 나 `_` 로 구성되지만 공백을 포함하지 못하며 숫자로 시작되서는 안된다.

<br>

### Storing Values with the Assignment Operator

자바스크립트에서 assignment operator를 활용해 변수에 value를 저장할 수 있다.

```javascript
var myVar = 5;
// Number value 5를 myVar에 assign했다.
```

Assignment는 항상 오른쪽에서 왼쪽으로 이루어진다. 항상 `=` operator의 오른쪽이 resolved 된후 왼쪽에 있는 변수에 그 value가 할당된다.

<br>

### Understanding Uninitialized Variables

자바스크립트에서 변수가 선언되면 이 변수들은 `undefined`라는 값을 가지게 된다. (Uninitialized Variable에 한해) 만일 `undefined` 변수를 토대로 수학 연산을 행하면 그 결과 "Not a Number"를 뜻하는 `NaN`를 얻게 될것이다. 만일 어떤 `string` 변수와 `undefined` 변수를 연결한다면 문자 그대로 `"undefined"`를 얻게 된다.

```javascript
var a;
console.log(a); // undefined가 출력된다.
a + 2; // NaN
a + "What?" // "undefinedWhat?"
```

<br>

### Understanding Case Sensitivity in Variables

자바스크립트내의 모든 변수명과 함수명은 case sensitive하다. 이말은 대문자와 소문자를 다르게 인식한다는 말이다. `MYVAR` 변수와 `MyVar` 변수는 다르다는 말.

자바스크립트는 이름을 짓는 방법에서 camelCase를 따른다. camelCase는 첫 문자는 소문자로 쓰고 그 뒤에 오는 단어들의 첫 글자는 대문자로 쓰는 방식이다.

```javascript
var someVariable;
var anotherVariableName;
var thisVariableNameIsSoLong;
```

<br>

### Math Operator with JavaScript

```javascript
var myNum = 5 + 10; // assign 15
myNum = 12 - 6; // assign 6
myNum = 13 * 13; // assign 169
myNum = 16 / 2; // assign 8
```

`++` operator를 사용하면 쉽게 변수에 1을 더할 수 있다.

`i++;` 는

`i = i + 1;` 과 같다.

`--` operator를 사용하면 쉽게 변수에 1을 뺄 수 있다.

`i--` 는 

`i = i - 1;` 과 같다.

나머지 operator `%` 는 숫자를 나눈후에 나머지를 반환한다.

```javascript
5 % 2 == 1 because
Math.floor(5 / 2) == 2 (Quotient)
2 * 2 == 4
5 - 4 == 1 (Remainder)
```

Tip: 나머지 연산자는 종종 modulus 연산자와 혼동되어 쓰이기도 하는데 modulus 연산자와 매우 흡사하지만 나머지 연산자는 음수에서는 정확히 작동하지 않는다.

<br>

### Create Decimal Numbers with JavaScript

또한 decimal number를 변수에 저장할 수 있다. decimal number는 종종 *float*이나 *floating point number*로 불리기도 한다. 

Tip: 모든 수들이 정확하게 floating point로 표현되는 것은 아니다. floating point로 숫자를 표현하게 되면 rounding error를 낳을 수도 있다.

```javascript
var product = 1.2 + 1.3 // assign 2.5
product = 2.5 - 1.2 // assign 1.3
product = 2.0 * 2.5 // assign 5.0
prouct = 4.4 / 2.0 // assign 2.2
```

<br>

### Compound Assignment With Augmented

프로그래밍에서 변수 값을 assign을 통해 변하게 하는 것은 흔한일이다. 

```javascript
var myNum = 10;
myNum = myNum + 5; // assign 15
```

이걸 더 간편하게 해주는 operators가 존재한다.

그 중 하나가 바로 `+=` operator이다.

```javascript
var myNum = 1;
myNum += 5;
console.log(myNum); // Returns 6
```

뺄셈에는 `-=` operator

```javascript
var myNum = 7;
myNum -= 5;
console.log(myNum); // Returns 2
```

곱하기에는 `*=`

```javascript
var myNum = 7;
myNum *= 5;
console.log(myNum); // Returns 35
```

나눗셈에는 `/=`

```javascript
var myNum = 10;
myNum /= 5;
console.log(myNum); // Returns 2
```

<br>

### Declare String Variables

```javascript
var myName = "your name";
```

`your name` 은 *string literal* 이라 불린다. 왜냐하면 이것은 0개 혹은 그 이상의 문자가 1개 혹은 2개의 따옴표에 에워쌓여 있기 때문이다.

만일 string안에 `"` 이나 `'` 를 표현하고 싶으면 앞에 `\` 를 앞에 붙혀주면 된다. 그리고 이를 *escape* 한다고 한다.

```javascript
var sampleStr = "Alan said, \"Peter is learning JavaScript\".";
```

<br>

###  Escape Sequences in Strings

Escaping 문자들을 사용하는데는 크게 2가지가 있다. 먼저 백 스페이스와 같이 입력 할 수없는 문자를 사용할 수 있기 때문이다. 두 번째는 자바 스크립트가 의미하는 바를 오해없이 문자열 안에서 나타낼 수 있게 하기 위해서다. 

| Code | Output          |
| :--- | :-------------- |
| `\'` | single quote    |
| `\"` | double quote    |
| `\\` | backslash       |
| `\n` | newline         |
| `\r` | carriage return |
| `\t` | tab             |
| `\b` | backspace       |
| `\f` | form feed       |

<br>

### Concatenating Strings

`+` operator가 String과 사용될 수 있습니다. 이것을 *concatenation* operator하고 합니다.

```javascript
var myStr= "This is the start." + " This is the end.";
console.log(myStr); // "This is the start. This is the end."
```

Tip: Concatenation은 자동으로 string사이에 공백을 넣지 않으므로 공백이 필요한 부분에는 스스로 공백을 집어넣어야 합니다.

또한 `+=` operator를 활용해 string을 concatenate할 수 있습니다.

```javascript
var myStr = "This is the first sentence. "
myStr += "This is the second sentence."
console.log(myStr); // "This is the first sentence. This is the second sentence."
```

String 사이에 변수를 집어 넣고 싶을 때, MadLibs style을 사용하기도 한다.

```javascript
var myName = "Park Choong Ho"
var myStr = "My name is " + myName + " and I am well!";
console.log(myStr);
// => "My name is Park Choong Ho and I am well!"
```

<br>

### Find the Length of a String

String변수나 String lieral뒤에 `.length` 을 붙여서 그 문자열의 길이를 받아올 수 있다.

```javascript
var firstName = "Choong Ho";
console.log(firstName.length); // 9
```

<br>

### Use Bracket Notation to Find the Character in a String

`Bracket notation`은 문자열로부터 특정 문자에 `index`를 통해 접근할 수 있게 하는 방법이다.

대부분의 프로그래밍 언어들은 사람과 다르게 0부터 숫자를 세기 시작한다. 이를 두고 *Zero-based* indexing이라한다.

```javascript
var firstName = "Charles";
console.log(firstName[0]); // C
console.log(firstName[4]); // l
```

string의 마지막 문자를 받아오고 싶으면 string.length - 1 index에 접근하면된다.

```javascript
var firstName = "Choong Ho";
firstName[firstName.length - 1]; // o
```

마찬가지로 뒤에서 n번째 문자를 받아오고 싶으면 string.length - n index로 접근한다.

```javascript
var firstName = "Choong Ho";
firstName[firstName.length - 4]; // g
```

<br>

## String Immutability

자바스크립트에서 `String` values는 immutable하다. (한번 생성되면 바뀔 수 없다는 뜻)

```javascript
var myStr = "Bob";
myStr[0] = "J";
console.log(myStr[0]); // "B"
```

`myStr` 변수를 "Job"으로 바꿀 수 없다. 왜내하면 `myStr`의 문자 값들은 바뀔 수 없기 때문이다. 그렇다고 `myStr` 변수 자체가 변할 수 없다는 것은 아니다. (다만 *string literal*의 개별 문자들은 변할 수 없다.)

```javaScript
var myStr = "Bob";
myStr = "Job";
```

이렇게 `myStr` 변수를 바꿀 수 있다.

<br>

### Store Multiple Values in one Variable using JavaScript Arrays

자바스크립트 `array`변수를 활용해 여러개의 데이터를 한곳에 모아서 저장할 수 있다.

```javascript
var sandwich = ["peanut butter", "jelly", "bread"];
```

또한 array안에 또 다른 array를 nest 할 수 있다. (`[["Bulls", 23], ["White Sox", 45]]`)

이걸 또한 *Multi-dimensional Array*라 부른다.

```javascript
var myArray = [["the universe", 42], ["everything", 101010]];
```

### Access Array Data with Indexes

array안에 있는 데이터에 `index`를 통해 접근할 수 있다. 이를 통해 특정 array안에 있는 특정 enrty에 접근할 수 있다. string과 마찬가지로 *zero-based* indexing을 사용한다. 따라서 첫번째 요소의 index는 0이다.

```javascript
var array = [50,60,70];
array[0]; // equals 50
var data = array[1]; // equals 60
```

Tip: array 변수명과 square brackets 사이에는 공백이 없어야 한다. 자바스크립트 코드가 이를 실행할 수는 있으나 다른 프로그래머가 코드를 읽는데 있어 가독성을 떨어트릴 수 있다.

<br>

### Modify Array Data With Indexes

string과 다르게 array의 각각의 entry들은 mutable해서 자유롭게 바꿀 수 있다.

```javascript
var ourArray = [50,40,30];
ourArray[0] = 15; // ourArray equals [15,40,30]
```

또한 *multi-dimensional* array에 접근할 수도 있다. *multi-dimensional* array에 접근할 때는 첫번째 brackets은 가장 바깥에 있는 entry와 동일하고 그 다음 brackets은 각각의 배열 안에 있는 그 다음 entry에 접근한다.

```javascript
var arr = [
    [1,2,3],
    [4,5,6],
    [7,8,9],
    [[10,11,12], 13, 14]
];
arr[3]; // equals [[10,11,12], 13, 14]
arr[3][0]; // equals [10,11,12]
arr[3][0][1]; // equals 11
```

<br>

### Manipulate Arrays 

`push()` array의 끝에 데이터를 append하는 method로 `push()` function이 있다. `push()` 는 한개 이상의 *parameter*를 받아와 이를 array의 끝에 push한다.

```javascript
// Example
var ourArray = ["Stimpson", "J", "cat"];
ourArray.push(["happy", "joy"]); 
// ourArray now equals ["Stimpson", "J", "cat", ["happy", "joy"]]

// Setup
var myArray = [["John", 23], ["cat", 2]];

myArray.push(["dog", 3]);
// myArray equals [["John", 23], ["cat", 2], ["dog", 3]]
```

`pop()` array의 맨 끝에 있는 entry를 가져온다. 이 entry를 변수에 할당해 저장할 수 있다. `.pop()` 은 array로부터 제거하고 그 요소를 return한다. 어떤 데이터 타입의 entry도 가져올 수 있다.

```javascript
var threeArr = [1, 4, 6];
var oneDown = threeArr.pop();
console.log(oneDown); // Returns 6
console.log(threeArr); // Returns [1, 4], 이렇게 array가 변화하게된다.
```

`shift()` 는 첫번째 요소를 array로부터 제거하고 가져올 수 있다. `pop()`과 똑같이 작동한다. 다른 점은 `shift()`는 첫번째 요소를 가져온다는 점이다.

```javascript
// Example
var ourArray = ["Stimpson", "J", ["cat"]];
var removedFromOurArray = ourArray.shift();
// removedFromOurArray now equals "Stimpson" and ourArray now equals ["J", ["cat"]].

// Setup
var myArray = [["John", 23], ["dog", 3]];

var removedFromMyArray = myArray.shift();
// myArray equals [["dog", 3]]
// removedFromArray equals ["John", 23]

```

`unshift()`를 사용해 array에 시작에 요소를 삽입할 수도 있다. `unshift()`는 `push()`랑 똑같이 작동하는데 array의 맨앞에 요소를 넣는 다는 점이 다르다.

```javascript
// Example
var ourArray = ["Stimpson", "J", "cat"];
ourArray.shift(); // ourArray now equals ["J", "cat"]
ourArray.unshift("Happy"); 
// ourArray now equals ["Happy", "J", "cat"]

// Setup
var myArray = [["John", 23], ["dog", 3]];
myArray.shift();

myArray.unshift(["Paul", 35]);
// myArray equals [["Paul", 35],["dog", 3]]
```

<br>

### Write Reusable JavaScript with Functions

자바스크립트에서는 *functions*라 불리는 reusable parts를 코드로부터 분리해 작성할 수 있습니다. 

```javascript
function functionName() {
  console.log("Hello World");
}
```

이런 함수를  이름 뒤에 `()`를 붙혀 부르거나 invoke함으로써 사용할 수 있습니다.

```javascript
functionName();
// Hello World, 함수가 불릴때마다 {} 안에 있는 코드를 실행하게 된다.
```

<br>

### Passing Values to Functions with Arguments

*Parameters* 는 함수가 불릴때마다 입력되는 입력값의 placeholder 처럼 작동하는 변수입니다. 함수가 실제로 불려질때 전달되는 값은 `arguments`라 불립니다.

```javascript
function testFun(param1, param2) {
    console.log(param1, param2);
} // 위 함수는 param1, param2라는 2개의 parameter값을 가진다.

testFun("Hello", "World"); // testFun 함수에 2개의 arguments "Hello", "World" 값을 전달했습니다. 함수를 다시 부를때, 다른 arguments 값을 줄 수 있습니다.
```

<br>

### Global Scope and Functions

*scope*는 변수의 visiblity입니다. 함수 바깥에서 선언된 변수는 Global scope를 가지게됩니다. 이말은, 이러한 변수는 자바스크립트 코드 어디에서든 쓰일 수 있다는 말과 같습니다. 변수가 선언될 때 앞에 `var`키워드 없이 선언되면 그 변수는 자동으로 global scope에 생성됩니다. 이는 나중에 다른 js파일이나 함수에서 의도치 않게 그 변수에 접근하거나 값을 수정할 수 있으므로, 변수를 선언할 때는 반드시 `var` 키워드를 붙여주도록 합시다.

```javascript
var myGlobal = 10;

function fun1() {
    oopsGlobal = 5;
}

function fun2() {
    var output = "";
    if (typeof myGlobal != "undefined") {
        output += "myGlobal: " + myGlobal;
    }
    if (typeof oopsGlobal != "undefined") {
        output += " oopsGlobal: " + oopsGlobal;
    }
    console.log(output);
}
```

<br>

### Local Scope and Functions

함수안에서 선언된 변수는 *local* scope를 가진다. (함수 parameter도 마찬가지) 따라서 이러한 변수들은 함수안에서만 visible하다. 

```javascript
function myTest() {
    var loc = "foo";
    console.log(loc);
}
myTest(); // logs "foo"
console.log(loc); // loc is not defined
```

local 변수와 global 변수가 같은 이름을 가질 수 있다. 이때는 `local`변수가 `global`변수에 우선한다.

```javascript
var someVar = "Hat";
function myFun() {
    var someVar = "Head";
    return someVar;
}
var str = myFun(); // myFun()는 "Head"를 리턴하게 된다. local 변수인 someVar이 존재하기 때문이다.
```

 <br>

### Return a Value from a Function with Return

argument를 통해 함수에 값을 전달할 수 있고 동시에 `return` statement을 통해 값을 함수 밖으로 전달할 수 있다.

```javascript
function plusThree(num) {
    return num + 3;
}
var answer = plusThree(5); // 8
```

함수는 `return` 구문을 가질 수 있지만 반드시 가질 필요는 없습니다. 만일 `return` 구문이 없는 함수를 부른다면 그 함수는 안에 코드를 실행하고 `undefined` 값을 return 하게 됩니다.

```javascript
var sum = 0;
function addSum(num) {
    sum = sum + num;
}
var returnedValue = addSum(3); // sum will be modified but returned value is undefined
```

함수로부터 return 된 값을 다시 변수에 할당할 수 있습니다.

```javascript
var changed = 0;

function change(num) {
  return (num + 5) / 3;
}

changed = change(10); // 5

var processed = 0;

function processArg(num) {
  return (num + 3) / 5;
}

processed = processArg(7); // 2
```

<br>

### Stand in Line

컴퓨터 공학에서 *quene* 는 데이터가 차례대로 저장되어 있는 추상적인 Data Structure을 일컫습니다. 새로운 데이터는 `quene` 데이터 뒤쪽에 추가될 수 있고 데이터가 제거될때는 `quene`앞에서 부터 제거됩니다. 

```javascript
function nextInLine(arr, item) {
  // Your code here
  arr.push(item);
  var removed = arr.shift();
  return removed;  // Change this line
}

// Test Setup
var testArr = [1,2,3,4,5];

// Display Code
console.log("Before: " + JSON.stringify(testArr));
console.log(nextInLine(testArr, 6)); // Modify this line to test
console.log("After: " + JSON.stringify(testArr));
```

<br>

### Use Conditional Logic with If Statements

`if` 키워드는 자바스크립트가 curly braces 안에 코드를 특정 조건안에 실행한다. ()안에 있는 condition이 `true` 이면 실행하게 된다. `false`이면 실행하지 않는다.

```pseudocode
if (condition is true) {
	statement is executed
}
```

```javascript
function test (myCondition) {
    if (myCondition) {
        return "It was true";
    }
    return "It was false";
}
test(true); // returns "It was true"
test(false); // returns "It was false"
```

<br>

### Comparison Operator

자바스크립트에는 여러 비교 연산자가 존재한다. 이 연산자들은 모두 `true` 아니면 `false`값을 return한다.

`==` , 이 equality operator는 두 값을 비교해서 둘이 같은면 `true`를 return 하고 다르면 `false`를 return 한다. 

```javascript
function equalityTest(myVal) {
    if (myVal == 10) {
        return "Equal";
    }
    return "Not Equal";
}

equalityTest(10); // return Equal
```

자바스크립트에서 서로 다른 두 데이터 타입을 비교하려면 두 데이터를 같은 타입으로 만들어 주어야 한다. 이걸 "Type Coercion"이라한다. 

```javascript
1 == 1 // true
1 == 2 // false
1 == '1' // true
"3" == 3 // true
```

<br>

### Strict Equality Operator

Strict equality ( `===` ) 는 `==` 연산자와 같은 역할을 수행한다. 하지만 `==`연산자와는 다르게 `===`연산자는 type conversion을 수행하지 않는다.

```javascript
3 === 3 // true
3 === '3' // false
```

Tip: 자바스크립트에서 특정 데이터의 type이 어떻게 되는지 알고 싶으면 `typeof`operator를 사용한다.

```javascript
typeof 3 // returns 'number'
typeof '3' // returns 'string'
```

<br>

### Inequality Operator

inequality operator(`!=`)는 `==`와 반대되는 개념이다. 비교되는 두값이 다르면 `true` 같으면 `false`를 return 한다. `!=` 연산자도 `==`와 마찬가지로 비교 실행시, data type을 변경한다.

```javascript
1 != 2 // true
1 != "1" // false
1 != '1' // false
1 != true // false
0 != false // false
```

`!==` Strict Inequality Operator는 `===`과 반대되는 개념이다. `===`와 마찬가지로 비교 실행시, data type을 변경하지 않는다.

```javascript
3 !== 3 // false
3 !== '3' // true
4 !== 3 // true
```

<br>

### Greater Than Or Equal To Operator

`>` operator는 두 값을 비교해 왼쪽 값이 더크면 `true` 아니면 `false`를 return 한다. `==`연산자처럼 `>` 연산자도 type conversion을 수행한다.

```javascript
5 > 3 // true
7 > '3' // true
2 > 3 // false
'1' > 9 // false
```

`greater than or equal to` 연산자 (`>=`) 는 2개 값을 비교해 왼쪽 값이 크거나 같으면 `true` 아니면 `false`를 리턴한다. `==` 연산자처럼 `>=` 연산자도 type conversion을 수행한다.

```javascript
6 >= 6 // true
7 >= '3' // true
2 >= 3 // false
'7' >= 9 // false
```

`less than or equal to` 연산자 (`<` `<=`)도 똑같이 작동한다. 

```javascript
2 < 5 // true
'3' < 7 // true
5 < 5 // false
3 < 2 // false
'8' < 4 // false

4 <= 5 // true
'7' <= 7 // true
5 <= 5 // true
3 <= 2 // false
'8' <= 4 // false
```

 <br>

### Logical Operator

`&&` operator는 연산자 기준 왼쪽과 오른쪽이 모두 `true` 이면 `true`를 리턴합니다.

```javascript
if (num > 5) {
    if (num < 10) {
        return "Yes";
    }
}
return "No";
```

`&&` 연산자를 사용하면 위 코드를 이렇게 바꿀 수 있습니다.

```javascript
if (num > 5 && num < 10) {
    return "Yes";
}
return "No";
```

`||` operator는 연산자 기준 왼쪽 혹은 오른쪽이 `true` 이면 `true`를 리턴합니다.

```javascript
if (num > 10) {
    return "No";
}
if (num < 5) {
    return "No";
}
return "Yes";
```

`||`연산자를 사용하면 위 코드를 이렇게 바꿀 수 있습니다.

```javascript
if (num > 10 || num < 5) {
    return "No";
}
return "Yes";
```

<br>

### Else Statements

만일 `if` statement 가 true면, 안쪽에 있는 코드가 실행되게 됩니다. 만약 false이면 아무일도 일어나지 않지만 `else` statement가 존재하면 그 안에있는 코드를 실행합니다.

```javascript
if (num > 10) {
    return "Bigger than 10";
} else {
    return "10 or Less";
}
```

<br>

### Else If Statements

다뤄야할 조건이 많을 경우에 `else if` 구문을 활용할 수 있습니다.

```javascript
if (num > 15) {
    return "Bigger than 15";
} else if (num < 5) {
    return "Smaller than 5";
} else {
    return "Between 5 and 15";
}
```

복잡한 logic을 `if/else` 문을 활용하여 제어할 수 있습니다.

```pseudocode
if (condition1) {
	statement1
} else if (condition2) {
	statement2
} else if (condition3) {
	statement3
. . .
} else {
	statementN
}
```

<br>

### Selecting from Many Options with Switch Statements

많은 options 중에서 하나를 골라야 할 때 `switch` statement를 사용합니다. `switch` 문은 많은 `case` statement를 가질 수 있습니다. 가장 먼저 matched된 `case` value를 만날때까지 `switch`문은 실행됩니다.

```pseudocode
switch(num) {
  case value1:
    statement1;
    break;
  case value2:
    statement2;
    break;
...
  case valueN:
    statementN;
    break;
}
```

`case` value들은 `===` 로 test됩니다. `break`를 만나면 코드 실행을 중단하고 빠져나오게 됩니다.

만일 여러 input에 대해서 같은 output을 내고 싶다면 이렇게 코드를 짤 수도 있습니다.

```pseudocode
switch(val) {
  case 1:
  case 2:
  case 3:
    result = "1, 2, or 3";
    break;
  case 4:
    result = "4 alone";
}
// 이 경우 1,2,3 case 모두 같은 "1, 2, or 3"라는 output을 낸다. 
```

<br>

### Adding a Default Option in Switch Statements

`switch` 문 안에서 match된 `case` value를 못 만날 수도 있습니다. 이경우 `default`문을 추가하면 `default`문 안에 있는 코드를 실행합니다. (`if/else`에서 마지막 `else`와 비슷한 기능을 합니다.) 

```pseudocode
switch (num) {
  case value1:
    statement1;
    break;
  case value2:
    statement2;
    break;
...
  default:
    defaultStatement;
    break;
}
```

<br>

### Returning Boolean Values from Functions

함수에서 if, else문을 사용하여 `true`나 `false`같은 boolean 값을 리턴할 수 있습니다.

```javascript
function isEqual(a,b) {
    if (a === b) {
        return true;
    } else {
        return false;
    }
}
```

위 코드를 아래와 같이 간소화해서 표현할 수 있습니다.

```javascript
function isEqual(a,b) {
    return a === b;
}
```

<br>

### Return Early Pattern for Functions

함수 내부에서 `return`문을 만나면 현 함수 실행은 중단되며, 그 함수가 호출되었던 위치로 다시 돌아갑니다.

```javascript
function myFun() {
    console.log("Hello");
    return "World";
    console.log("byebye")
}
myFun();
```

위 결과는 "Hello"를 console에 출력하고 "World" 문자열을 return합니다. "byebye"는 출력되지 않습니다. 출력하기전에 return문을 만나기 때문입니다.

<br>

### Generate Random Fractions with JavaScript

Random numbers are useful for creating random behavior.

JavaScript has a `Math.random()`function that generates a random decimal number between `0`(inclusive) and not quite up to `1`(exclusive). Thus `Math.random()`can return a `0`but never quite return a `1`.

It's great that we can generate random decimal numbers, but it's even more useful if we use it to generate random whole numbers.

1. random decimal숫자를 생성하기 위해 `Math.random()`를 사용합니다.
2. 그 숫자에 20을 곱합니다.
3. `Math.floor()` 을 사용해 소숫점 이하를 버려 정수로 만듭니다.

```javascript
var randomNumberBetween0and19 = Math.floor(Math.random() * 20);

function randomWholeNum() {
    return Math.floor(Math.random()*10);
}
```

<br>

### Generate Random Whole Numbers within a Range

특정 숫자 범위 예를 들어 2와 10사이의 숫자 범위를 설정할 수도 있습니다. 따라서 범위 설정에서 작은 숫자를 `min`으로 두고 큰 숫자는 `max`로 두겠습니다.

```javascript
Math.floor(Math.random() * (max - min + 1)) + min
```

위 코드를 통해 우리는 min과 max사이에 숫자를 random하게 받을 수 있습니다.

<br>

### Use the parseInt Function

`parseInt()` 함수는 문자열을 parsing후 integer로 리턴합니다.

```javascript
var a = parseInt("007");
// a는 integer 7 값을 가진다.
```

만약 문자열의 첫번째 문자가 숫자로 변환될 수 없으면 `NaN`을 리턴합니다.

`parseInt()` 함수는 두번째 argument로 radix를 받습니다. 

(radix는 진수를 나타냅니다. 2와 36사이의 값)