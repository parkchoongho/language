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

