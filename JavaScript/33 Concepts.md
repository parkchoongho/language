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