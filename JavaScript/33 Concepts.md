## 1. Call Stack

Call Stack은 자바스크립트가 함수 실행을 핸들링하는 방법 중 하나이다. 자바스크립트는 실행할 함수들을 스택(stack)위에 올린다. 스택은 일종에 쌓아올라가는 것을 생각하면 된다.(책을 쌓는다거나, 카드 스택을 만드는 등등)

함수를 실행할 때마다 위에서부터 실행하고 하나씩 스택을 제거해나간다.

```javascript
function three(){
    console.log('I love JS')
}

function two(){
    three();
}

function one(){
    two();
}

function zero(){
	one();
}

zero();
```

Call Stack 쌓이는 순서: zero => one => two => three

Call Stack 사라지는 순서: three => two => one => zero

```javascript
function three(){
    console.log('I love JS')
}

function two(){
    three();
}

function one(){
    two();
}

function zero(){
	one();
    throw Error("omg i am an error")
}

zero();
```

one 함수가 call stack에서 사라지고 난 다음(one 함수가 실행되고 종료된 후, 에러가 발생한다.)

**Tip:** 에러 메세지를 보면 에러전에 있었던 모든 콜스택을 알려준다. + 스택이 붕괴될 때 에러가 나는 현상이 있다. (Maximum call stack size exceeded) 자바스크립트 스택에는 올릴 수 있는 제한이 있다.

```javascript
function hello(){
	bye();
}
function bye(){
    hello();
}
hello();
```

<br>

## 2. Primitive Types

Primitive는 말 그대로 기초적인, 원시적인 이란 뜻이다.

총 7가지가 존재하는데,

`undefined`,  `null`,  `boolean`,  `string`,  `symbol`,  `number`,  `object`

`undefined`와 `null`이 많은 혼란을 불러일으킨다. `undefined` 는 '정의가 되지 않음' 이라는 뜻이고 `null` 은 '존재하지 않음으로 정의됨'을 의미한다.

```javascript
let hello;
console.log(hello);
=> undefined, 선언은 됐으나 정의되지 않았으므로 undefined이다.
console.log(hello === null);
=> false, null은 존재하지 않음 이라는 하나의 값이므로 false이다.
hello = null;
console.log(hello === null);
=> true, null 값을 할당해서 정의해줬으므로 true이다.
```

**cf)** NaN이란? 약어로 Not A Number라는 뜻이다.

```javascript
Math.pow(5, "hello");
=> NaN이 나온다. 이렇게 이상한 수학 공식을 작성하면 NaN 값을 준다.
```

<br>

## 3. Value Types and Reference Types

```javascript
let a = 50;
let b = a;

a = 10;
console.log(b);
```

이렇게 하면 콘솔에 50이 뜬다. 왜냐하면 `let b = a` 를 할 때, a의 **value**를 복사하기 때문이다. 따라서 이것은 참조하는 Reference와는 다르다.

```javascript
const sexy = ["kimchi", "potato"];
const pretty = sexy;

console.log(pretty);

sexy.push("bulgogi");

console.log(pretty);
```

=> 위는 `["kimchi", "potato"]`가 나타나고 아래는 `["kimchi", "potato", "bulgogi"]`가 나타난다. 이것을 Reference라 부른다. pretty를 업데이트 하지 않았지만 프리티가 업데이트 되었다. 따라서 이것은 값을 복사하는 것이 아닌, Referencing한 것이다.

위에서 sexy의 값이 `["kimchi", "potato"]` 가 되는 것이 아니라, sexy는 `["kimchi", "potato"]` 를 참조하고 있는 것이다. 그리고 pretty는 sexy와 같은 것을 참조하고 있기에 sexy가 참조하는 배열이 업데이트 되면 pretty에도 반영되는 것이다.

```javascript
console.log([10] === [10]);
```

둘은 각각 메모리에 위치한 다른 object이므로 false를 출력한다.

**Tip:** Value는 string, number, boolean, NaN, undefined, null, symbol에서 가능하고 Reference는 array, object, function에서 사용될 수 있다.

<br>

## 4. Type Coercion

```javascript
console.log(4 + "hello");
console.log(4 + 4 + "hello");
console.log("" == true);
console.log(1 == true);
console.log(66 + true);
// 4hello
// 8hello
// false
// true
// 67
```

자바스크립트는 최대한 에러가 발생하지 않는 방향으로 개발했기에 위와 같은 결과가 나온다.

#### Type Coercion

Type Coercion (or Conversion)은 자바스크립트가 강제적으로 값을 변환시킨다는 뜻이다.

`console.log(66 + true)` 코드를 자바스크립트가 만나면, true를 1로 변환시키기 때문에 67이 출력된다. (false는 0으로 변환된다.)

하지만 더하기가 항상 숫자로 변환시키는 것은 아니다. `console.log(66 + "false")` 이 코드를 작성하면 66false가 결과로 나온다. 여기서는 66을 string으로 바꿔준다. (오직 더하기에서만 이렇게 작동하고 이를 loaded operator라고 한다.)

```javascript
console.log(11 + 55 + "false");
// 66false 출력. 왜냐하면 자바스크립트는 왼쪽에서 오른쪽으로 코드를 읽어내려가기 때문이다.
console.log(25 - "1");
// 24 출력 
```

```javascript
console.log("" == true);
console.log(0 == true);
console.log(NaN == true);
console.log(undefined == true);
console.log(null == true);
```

`===` 를 사용해서 비교하면 Type Coercion이 일어나지 않는다.

```javascript
console.log(1 == "1");
// true
console.log(1 === "1");
// false
console.log("true" == true)
// false
```

`console.log("true" == true)` 가 거짓인 이유는?

== 는 boolean을 만나면 숫자로 변환한다. "true"도 숫자로 바꾸려하지만 `NaN `이 된다.

결과적으로 `console.log(NaN == 1)` 이 되며 false를 출력한다.

== 는 이렇게 예기치 못한 결과를 낳을 수 있으므로 === 를 사용하는 것을 생활화 하는 것이 좋다.

```javascript
const hello = "";
if(typeof hello !== undefined){
    console.log("hello");
}
// hello는 undefined가 아니기 때문에 hello를 출력한다.
```

<br>

## 5. Typeof

Typeof는 데이터가 어떤 타입을 가지는지 알고 싶을 때 사용한다.

```javascript
console.log(typeof 1);
// number 출력
console.log(function(){});
// function 출력
```

그런데 typeof에도 예기치 못하게 발생하는 에러가 있다.

```javascript
console.log(typeof null);
// object 출력
```

그래서 이걸 고치겠다는 논의가 진행되었으나 이미 JavaScript로 작성된 많은 프로그램들이 영향을 받을까봐 고쳐지지는 않았다.

이외에도 몇 가지 버그가 더 있다.

```javascript
console.log(typeof []);
// object 출력
console.log(typeof {});
// object 출력
```

Array인지 Object인지 체크하고 싶은데 둘다 Object로 나온다. 이런 경우에는 typeof 대신 instanceof를 사용한다. (instanceof는 primitive type에서는 적용되지 않는다.)

```javascript
console.log([] instanceof Array);
// true 출력
console.log({} instanceof Array);
// false 출력
console.log([] instanceof Object);
// true 출력
console.log({} instanceof Object);
// true 출력
```

number, string, boolean, undefined, function등을 체크하고 싶으면 typeof를 사용한다.

<br>

## 6. Function Scope, Block Scope and Lexical Scope

Scope는 선언한 Variable이 존재하는가?(정의가 되었나)에 대한 답이다.

```javascript
if(true){
	const hello = "Hi!";
}

console.log(hello);
// error 발생 hello is not defined
```

hello는 자신이 속한 { }안에서만 존재한다.

```javascript
const h = "hello";

function a(){
	console.log(h);
	const b = "b";
}

a();
console.log(b);
```

hello는 출력되지만 변수 b는 a 함수 { }안에서 선언되었으므로 외부에서 접근할 수 있습니다.

```javascript
if(true){
	var hello = "h";
}

console.log(hello);
// h 출력
```

여기서는 h가 출력된다. 이것이 var를 써서는 안되는 이유이다. let, const는 block scope이다. (let, const는 선언된 scope안에서만 접근이 가능하다.)

개발자로 일을 할 때는 Scope를 공유해야 할때가 있다.

```javascript
let hello;
if(true){
	hello = "hello";
}
console.log(hello)
```

<br>

## 7. Expression vs Statement

**Expression**이란, value를 리턴하는 무언가를 의미한다.

```javascript
5 + 1
```

JavaScript에서는 위를 expression이라 부른다. (위 값을 6으로 return한다.) 무엇이든 value 를 return 하는 것은 expression이다.

```javascript
function add(a, b){
    return a + b;
}
const addedNumber = add(5, 6);
```

위 코드에서 `add(5,  6)`는 expression이다. 함수 부분에서 return이 없어도 expression이다. (undefined를 return하기 때문이다.) JavaScript는 expression을 value로 교체하고 계속 진행해 나간다.

**Statement** 란, 명령 혹은 지시를 뜻한다.

```javascript
if(true){
    // bla bla bla
}
```

statement는 variable에 할당할 수 없다.

```javascript
const thing = if(true){
    // bla bla bla
}
```

위 같이 코드를 작성하면 에러가 발생한다. (= 연산자 때문에 expression을 기대하고 있다.)

cf) **Function Declaratoin & Function Expression**

```javascript
const addedNumber = add(1, 5);

function add (a, b){
    return a + b;
}

console.log(addedNumber);
// 6이 출력됨. 작동한다.
```

`function add (a, b){`
    `return a + b;`
`}`

이 코드 부분은 declaration이다. JavaScript는 declaration을 보면 이를 코드 상단부로 가져온다. (이건 hoisting이라는 프로세스다.)

```javascript
const addedNumber = add(1, 5);

const add = (a, b) => a + b;

console.log(addedNumber);
// 에러 발생 (Not defined Error)
```

에러가 발생한다. (Not defined Error) 왜냐하면 `const add= (a, b) => a + b;` 는 **declaration이 아닌, expression이기 때문이다.**

<br>

## 8. IIFE & Modules

IIFE(Immediate-Invoked Function Expressions)