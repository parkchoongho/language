# 1. Why JS?

JavaScript는 웹에서 쓰이는 유일한 프로그래밍 언어

Backend에는 많은 옵션들이 존재(Python, Ruby, 하스켈, ASP,...etc)

But, Frontend는 바로 JavaScript로 해야한다. 

<br>

<br>

# 2. ES5, ES6 ?

ECMAScript의 준말이며 일종의 Specification이다.

**(Specification이 머지?)**

=> JavaScript는 중앙 집중화가 잘 되어있어 누군가 업데이트를 하면 모든 브라우저에서 작동하게 된다. 이렇게 JavaScript는 일종의 체계 메뉴얼을 갖추고 있는데 이를 두고 Specification이라 한다. 이를 다른발로 ECMAScript라 하는 것이다. 각각의 브라우저 마다 이 Specification을 받아 다르게 해석한다. 

뒤에 붙는 숫자는 ECMAScript의 버전 업데이트를 말하는 것이다. 

<br>

<br>

# 3. Vanilla JavaScript

Vanilla JavaScript는 JavaScript의 일종으로 라이브러리가 없는 JavaScript를 이야기한다.

(브라우저를 통해 제공된 JavaScript라 보면 편하다.)

JavaScript는 프로그래머가 나쁜 코드를 작성하는 것을 허용한다. 

각각의 Instruction은 다른 줄에 존재한다. (이런 한줄에 존재하는 것을 **Expression**이라 부른다.) <br>Expression은 한줄에 존재해야한다. 한 Expression이 끝났다는 것은 **';'**을 마지막에 붙혀 표현한다.

<br>

### 변수 사용법

Create - Initialize - Use

어떤 변수가 값이 변하지 않기를 원한다면 변수 앞에 **const**라고 쓴다. **const**는 constant의 준말로 상수라는 뜻이다. (변하지 않는 수)

```javascript
const a = 221;
const b = a - 5;
a = 4; //이러면 에러가 발생한다. 왜냐하면 a는 변할 수 없는 고정값이기 때문에.
```

반대로 let으로 변수를 선언하면 계속해서 값을 바꿀 수 있다.

```javascript
let a = 221;
let b = a - 5;
a = 4; //에러가 발생하지 않는다. 왜냐하면 let으로 변수를 선언했기 때문에.
```

=> 기본적으로 변수 선언은 const로 할 것. 나중에 필요할 때만 let으로 선언.

변수 선언시 Camel case 방식으로 변수를 작성해야 한다.

```javascript
const dayOfWeek = "월"// 변수명은 소문자로 시작해서 스페이스가 필요한 중간 중간 대문자로 써주는 방법이다.
```

<br>

### Data Types

String, Number, Boolean, Float

```javascript
const string = "ABC";
const number = 9;
const boolean = true;
const float = 55.1; // float은 언제나 floating number(떠돌이 소숫점)을 가진다.

```

<br>

### How to organize data in JavaScript?

<br>

1) Array

선언 방법

```javascript
const daysOfWeek = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];

console.log(daysOfWeek[0]); //특정값에 대해 접근하려면 index로 접근해야한다.
```

<br>

2) Object

선언방법

```javascript
const nicoInfo = {
	name: "Nico",
    age: 33,
    gender: "Male",
    isHandsome: true
};

console.log(nicoInfo.name);// name에 접근하고 싶으면 이렇게 접근한다.

nicoInfo.gender = "Female"; // 이렇게 const nicoInfo안에 있는 값을 바꿀 수 있다. 하지만 nicoInfo자체는 바꿀 수 없다.

console.log(nicoInfo.name);
```

Object와 Array의 가장 큰 차이점은 Object는 각 value에 이름을 붙힌다는 점이다.

<br>

Object안에 Array를 넣을 수도 있고 Array안에 Object를 넣을 수도 있다.

```javascript
const fav = {
    favMovies: ["Along the Gods", "LOTR", "Oldboy"],
    favFood:  [
      {
        name: "Kimchi",
        fatty: false
    },{
        name: "Cheeseburger", 
        fatty:true
    }
    ]
}
```

<br>

### What is function?

함수는 어떤 내용을 수행하는 부분으로서 원하는 만큼 쓸 수 있는 코드로 생각하면 된다.

```javascript
function sayHello(name) {
  console.log(`Hello ${name}!`);
}

sayHello("Park");
```

<br>

### Argument

```javascript
function sayHello(name) {
  console.log(`Hello ${name}!`);
}

sayHello("Park");
```

여기서 sayHello() 함수에 전달되는 "Park"을 argument라고 한다. 함수가 정의되어 있을 때 같이 선언되어 있는 name은 parameter라 한다.(이 2개 용어를 혼용해서 사용하기도 한다.)

=> "Park"값을 name에 넣고 이 name을 활용한 코드를 실행한다.

```javascript
function sayHello(name, age) {
  console.log(`Hello ${name}! I am ${age} years old!`);
}

sayHello("Park", 28);
```

이렇게 argument를 2개로 줄 수도 있고 argument는 갯수에 구애받지 않고 가질 수 있다.

<br>

### 함수를 활용한 간단한 계산기 객체

```javascript
const calculator = {
    plus: function(a, b) {
        return a + b;
    },
    minus: function(a, b) {
        return a - b;
    },
    multiply: function(a, b) {
        return a * b;
    },
    divide: function(a, b) {
        return a / b;
    },
    exponent: function(a, b) {
        return a ** b;
    }
};

const plus = calculator.plus(5, 5);
const minus = calculator.minus(5, 5);
const multiply = calculator.multiply(5, 5);
const divide = calculator.divide(5, 5);
const exponent = calculator.exponent(5, 5);

console.log(`
Plus: ${plus}
Minus: ${minus}
Multiply: ${multiply}
Divide: ${divide}
Exponent: ${exponent}
`);

```

<br>

### DOM (Document Object Model)

document는 하나의 객체로서 자바스크립트가 html 파일 요소에 접근할 수 있게 해준다. html 태그를 가져다가 객체로 만든다.

```javascript
const title = document.getElementById("title");
console.log(title);
```

```javascript
const title = document.getElementById("title");
console.dir(title);
```

위 코드를 통해 title객체안에 있는 key와 value들을 모두 확인할 수 있다.

```javascript
const title = document.querySelector("#title"); // id로 찾아 가장 첫번째 노드를 반환.
const title = document.querySelector(".title"); // class로 찾아 가장 첫번째 노드를 반환.
```

querySeletor는 관련 노드 중 첫번째 노드를 반환한다.

<br>

### Event

이벤트는 웹사이트 상에서 발생할 수 있는 것들을 말한다. (Click, Resize, Submit, Load 등등)

우리는 이러한 이벤트들을 중간에서 가져올 수 있다.

```javascript
window.addEventListener("resize")
```

=>  이게 우리가 이벤트를 받기를 기다리는 것이다. (Listen to Event) 위 코드 예시는 자바스크립트가 window가 resize하기를 기다리고 있다는 뜻!!

```javascript
const title = document.querySelector("#title");

function handleResize() {
  console.log("I have been resized");
}

window.addEventListener("resize", handleResize);
```

window를 resize하면 handleResize 함수를 호출한다.

```javascript
window.addEventListener("resize", handleResize);
```

여기서 체킹할  사항

**handleResize()가 아니다.** handleResize); 는 **내가 필요할 때 (윈도우 크기가 변경될 때) handleResize라는 함수를 호출**하는 것이다. **handleResize()는 지금 당장 호출**하는 것이다.

<br>

```javascript
const title = document.querySelector("#title");

function handleResize(event) {
  console.log(event);
  //console.log("I have been resized");
}

window.addEventListener("resize", handleResize);
```

=> **이벤트를 다룰 함수를 만들때 마다 자바스크립트는 자동적으로 함수를 객체에 붙힌다.**  **event가 발생할 때** 마다 이 **event 객체가 호출**된다. 

이벤트에 대해서 알아보고 싶으면 이 사이트를 확인하자.

<https://developer.mozilla.org/ko/docs/Web/Events>

<br>

### 이벤트 예시

```javascript
function handleOffline() {
  console.log("인터넷 연결이 끊어졌습니다.");
}

function handleOnline() {
  console.log("인터넷에 연결되었습니다.");
}

window.addEventListener("offline", handleOffline);
window.addEventListener("online", handleOnline);
```

이벤트 예시) 인터넷 연결을 감지할 수 있는 코드

<br>

### 코드 별 분리

기본적으로 html은 html에서 css는 css에서 해결하고 javascript는 로직만 담당하는 코드가 좋다. 이런 시각에서 밑의 코드는 그다지 좋은 코드가 아니다.

```javascript
const title = document.querySelector("#title");

const BASE_COLOR = "rgb(52, 73, 94)";

const OTHER_COLOR = "#7f8c8d";

function handleClick() {
  const currentCOLOR = title.style.color;
  if (currentCOLOR === BASE_COLOR) {
    title.style.color = OTHER_COLOR;
  } else {
    title.style.color = BASE_COLOR;
  }
}

function init() {
  title.style.color = BASE_COLOR;
  title.addEventListener("click", handleClick);
}

init();
```

왜냐하면 자바스크립트를 통해 css를 제어하고 있기 때문이다. 따라서 위 코드를 이렇게 바꾸는 것이 더 좋은 코드이다.

<br>

```css
body {
  background-color: #ecf0f1;
}

.btn {
  cursor: pointer;
}

h1 {
  color: #34495e;
  transition: color 2s ease-in-out;
}

.clicked {
  color: #7f8c8d;
}
```

```javascript
const title = document.querySelector("#title");

const CLICKED_CLASS = "clicked";

function handleClick() {
  const classList = title.classList;
  //console.log(currentClass);
  if (classList.contains(CLICKED_CLASS)) {
    //console.log(currentClass);
    classList.remove(CLICKED_CLASS);
  } else {
    //console.log(currentClass);
    classList.add(CLICKED_CLASS);
  }
}

function init() {
  title.addEventListener("click", handleClick);
}

init();
```

이렇게 바꾸면 자바스크립트 코드에서는 프로그램 흐름만 제어하고 css는 css 코드에서만 다루기 때문에 알아보기가 훨씬 쉽다.

참고로 위 자바스크립트 코드는 이렇게 바꿀 수 있다.

```javascript
const title = document.querySelector("#title");

const CLICKED_CLASS = "clicked";

function handleClick() {
  title.classList.toggle(CLICKED_CLASS);// 클래스 리스트에서 CLICKED_CLASS가 있으면 이를 지우고 없으면 그 클래스를 더한다.
}

function init() {
  title.addEventListener("click", handleClick);
}

init();
```

<br>

### 삼항연산자(Ternary Operator)

삼항연산자를 활용해 if문을 string 한줄에 적을 수 있다.

```javascript
clockTitle.innerText = `${hours < 10 ? `0${hours}` : hours} : ${
    minutes < 10 ? `0${minutes}` : minutes
  } : ${seconds < 10 ? `0${seconds}` : seconds}`;

// hours < 10 는 조건문이고 만일 이 조건문이 참이면 : 표시를 기준으로 앞에 있는 값을 리턴하고 거짓을 경우에는 뒤에 있는 값을 리턴한다.
```

