# JavaScript

### Why JS?

JavaScript는 웹에서 쓰이는 유일한 프로그래밍 언어입니다.

Backend에는 많은 옵션들이 존재(Python, Ruby, 하스켈, ASP,...etc)하지만

But, Frontend는 JavaScript밖에 선택지가 없습니다.

### ES5, ES6 ?

ECMAScript의 준말이며 일종의 Specification입니다.

**(Specification이 머지?)**

=> JavaScript는 중앙 집중화가 잘 되어있어 누군가 업데이트를 하면 모든 브라우저에 업데이트 내역이 적용됩니다. 이렇게 JavaScript는 일종의 체계 메뉴얼을 갖추고 있는데 이를 두고 Specification이라 부릅니다. 이를 다른 말로 ECMAScript라 합니다. 각각의 브라우저 마다 이 Specification을 받아 다르게 해석하는 특징을 가지고 있습니다.

뒤에 붙는 숫자는 ECMAScript의 버전 업데이트를 의미합니다.

### Vanilla JavaScript

Vanilla JavaScript는 JavaScript의 일종으로 라이브러리가 없는 JavaScript를 말합니다.

(브라우저를 통해 제공된 JavaScript라 보면 됩니다.)

JavaScript는 프로그래머가 나쁜 코드를 작성하는 것을 허용합니다.

또 다른 특징으로 자바스크립트 각각의 Instruction은 다른 줄에 존재합니다. (한줄에 존재하는 코드를 **Expression**이라 부릅니다.) 한 Expression이 끝났다는 것을 **';'**를 마지막에 붙혀 나타냅니다.

### 변수 사용법

Create - Initialize - Use

어떤 변수가 값이 변하지 않기를 원한다면 변수 앞에 **const**라고 씁니다. **const**는 constant의 준말로 상수라는 의미입니다. (변하지 않는 수)

```javascript
const a = 221;
const b = a - 5;
a = 4; //이러면 에러가 발생합니다. 왜냐하면 a는 변할 수 없는 고정값이기 때문입니다.
```

반대로 let으로 변수를 선언하면 계속해서 값을 변경할 수 있습니다.

```javascript
let a = 221;
let b = a - 5;
a = 4; //에러가 발생하지 않습니다. 왜냐하면 let으로 변수를 선언했기 때문입니다.
```

=> 기본적으로 변수 선언은 const로 할 것. 나중에 필요할 때만 let으로 선언.

변수 선언시 Camel case 방식으로 변수를 작성해야 합니다.

```javascript
const dayOfWeek = "월"; // 변수명은 소문자로 시작해서 스페이스가 필요한 중간 중간 대문자로 써주는 방법 (Camel Case).
```

### Data Types

String, Number, Boolean, Float

```javascript
const string = "ABC";
const number = 9;
const boolean = true;
const float = 55.1; // float은 언제나 floating number(떠돌이 소숫점)을 가지게 됩니다.
```

### How to organize data in JavaScript?

1. Array

선언 방법

```javascript
const daysOfWeek = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"];

console.log(daysOfWeek[0]); //특정값에 대해 접근하려면 index로 접근.
```

2. Object

선언방법

```javascript
const nicoInfo = {
  name: "Nico",
  age: 33,
  gender: "Male",
  isHandsome: true
};

console.log(nicoInfo.name); // name에 접근.

nicoInfo.gender = "Female"; // 이렇게 const nicoInfo안에 있는 값을 변경할 수 있지만 nicoInfo자체는 변경 불가.

console.log(nicoInfo.name);
```

Object와 Array의 가장 큰 차이점은 Object는 각 value에 이름이 붙는다는 점입니다.

Object안에 Array를 넣을 수 있고 Array안에 Object를 넣을 수도 있습니다.

```javascript
const fav = {
  favMovies: ["Along the Gods", "LOTR", "Oldboy"],
  favFood: [
    {
      name: "Kimchi",
      fatty: false
    },
    {
      name: "Cheeseburger",
      fatty: true
    }
  ]
};
```

자바스크립트 객체에 저장할 때 Key 값과 Value 값이 같으면 이런 문법을 적용할 수 있습니다.

```javascript
const lat = position.coords.latitude;
const lon = position.coords.longitude;
const coordsObj = {
  lat,
  lon // lat: lat, lon: lon과 같은 코드.
};
```

### What is function?

함수는 어떤 내용을 수행하는 부분으로서 원하는 만큼 쓸 수 있는 코드라 생각하면 됩니다.

```javascript
function sayHello(name) {
  console.log(`Hello ${name}!`);
}

sayHello("Park");
```

### Argument

```javascript
function sayHello(name) {
  console.log(`Hello ${name}!`);
}

sayHello("Park");
```

여기서 sayHello() 함수에 전달되는 "Park"을 argument라고 합니다. 함수가 정의되어 있을 때 같이 선언되어 있는 name은 parameter라 합니다.(이 2개 용어를 혼용해서 사용하기도 합니다.)

=> "Park"값을 name에 넣고 이 name을 활용한 코드를 실행합니다.

```javascript
function sayHello(name, age) {
  console.log(`Hello ${name}! I am ${age} years old!`);
}

sayHello("Park", 28);
```

이렇게 argument를 2개로 줄 수도 있고 argument는 갯수에 구애받지 않고 가질 수 있습니다.

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

### DOM (Document Object Model)

document는 하나의 객체로서 자바스크립트가 html 파일 요소에 접근할 수 있게 해준다. html 태그를 가져다가 객체로 만듭니다.

```javascript
const title = document.getElementById("title");
console.log(title);
```

```javascript
const title = document.getElementById("title");
console.dir(title);
```

위 코드를 통해 title객체안에 있는 key와 value들을 모두 확인할 수 있습니다.

```javascript
const title = document.querySelector("#title"); // id로 찾아 가장 첫번째 노드를 반환.
const title = document.querySelector(".title"); // class로 찾아 가장 첫번째 노드를 반환.
```

querySeletor는 관련 노드 중 첫번째 노드를 반환합니다.

```javascript
const title = document.querySelectorAll(".title"); // queryselectorAll은 모든 요소들을 가져와서 배열형태로 전달.
```

querySelectorAll은 모든 요소를 가져와 배열형태로 저장합니다.

### Event

이벤트는 웹사이트 상에서 발생할 수 있는 것들을 의미합니다. (Click, Resize, Submit, Load 등등)

우리는 이러한 이벤트들을 중간에서 가져올 수 있습니다.

event가 발생하면 발생했던 그 요소부터 document까지 올라갑니다.

```javascript
window.addEventListener("resize");
```

=> 해당 코드가 이벤트를 받기를 기다립니다. (Listen to Event) 위 코드 예시는 자바스크립트 객체 window가 resize하기를 기다리고 있다는 뜻!!

```javascript
const title = document.querySelector("#title");

function handleResize() {
  console.log("I have been resized");
}

window.addEventListener("resize", handleResize);
```

window를 resize하면 handleResize 함수를 호출합니다.

```javascript
window.addEventListener("resize", handleResize);
```

여기서 체킹할 사항

**handleResize()가 아닌 것을 확인할 수 있습니다.** handleResize(); 는 **내가 필요할 때 (윈도우 크기가 변경될 때) handleResize라는 함수를 호출**하는 것입니다. **handleResize()는 지금 바로 함수를 호출**하는 것을 의미합니다.

```javascript
const title = document.querySelector("#title");

function handleResize(event) {
  console.log(event);
  //console.log("I have been resized");
}

window.addEventListener("resize", handleResize);
```

=> **이벤트 핸들링 함수를 만들 때 자바스크립트는 자동으로 함수를 객체에 붙힙니다.** **event가 발생할 때** 마다 이 **event 객체가 호출**됩니다.

이벤트에 대해서 더 궁금하신 분들은 아래의 링크를 확인하시면 좋습니다.

<https://developer.mozilla.org/ko/docs/Web/Events>

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

```javascript
function handleSubmit(event) {
  event.preventDefault(); // event 객체의 preventDefault method를 호출.
}

form.addEventListener("submit", handleSubmit);
```

또 다른 예시) form 태그의 submit event가 발생할 때 기본 동작을 막는 코드 (form 태그내 input에 값을 입력하고 Enter를 쳐도 입력값이 사라지지 않습니다.)

### 코드 별 분리

기본적으로 html은 html, css는 css끼리 묶고 javascript는 로직만 담당하는 코드가 좋습니다. 이런 시각에서 보면 밑의 코드는 그다지 좋은 코드가 아님을 알 수 있습니다.

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

자바스크립트를 통해 css를 제어하고 있습니다. 아래와 같이 코드를 변경해 봅시다.

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

이렇게 자바스크립트와 css를 분리해 놓았기에 알아보기도 쉽고 유지보수 측면에서도 장점을 가지게 됩니다.

위 자바스크립트 코드는 아래와 같이 더 간단히 변경할 수 있습니다.

```javascript
const title = document.querySelector("#title");

const CLICKED_CLASS = "clicked";

function handleClick() {
  title.classList.toggle(CLICKED_CLASS); // 클래스 리스트에 CLICKED_CLASS가 있으면 지우고 없으면 그 클래스를 더하는 코드.
}

function init() {
  title.addEventListener("click", handleClick);
}

init();
```

### 삼항연산자(Ternary Operator)

삼항연산자를 활용하면 if문을 더 간단히 작성할 수 있습니다.

```javascript
clockTitle.innerText = `${hours < 10 ? `0${hours}` : hours} : ${
  minutes < 10 ? `0${minutes}` : minutes
} : ${seconds < 10 ? `0${seconds}` : seconds}`;

// hours < 10 는 조건문이고 만일 이 조건문이 참이면 : 표시를 기준으로 앞에 있는 값을 리턴하고 거짓을 경우에는 뒤에 있는 값을 리턴.
```

### Local Storage

Local Storage는 정보를 유저 컴퓨터에 저장하는 방법 중 하나입니다.

브라우저에서 F12키를 누르고 Application 탭을 선택하면 확인할 수 있습니다.

```javascript
localStorage.setItem("nico", true); // 이렇게 코드를 작성하면 nico라는 키값에 true라는 value값이 설정됩니다. localStorage에 정보를 생선하는 방법.
localStorage.getItem("nico"); // localStorage로부터 nico 키값에 해당하는 value값을 가져오는 코드.
```

Local Storage는 URLs 를 기초로 동작합니다. (해당 url의 localStorage에만 접근 가능)

### 자바스크립트 객체 Local Storage에 저장하기

local storage에는 자바스크립트 data를 저장할 수 없습니다. **local storage**에는 **오직 String형태**만 저장됩니다. 따라서 local storage 저장시에는 데이터를 String으로 변경 후 저장합니다.

```javascript
function saveToDos() {
  localStorage.setItem(TODO_LS, JSON.stringify(toDos)); // toDos is array
}
```

`JSON.stringify()` 코드는 데이터를 JSON 문자열로 변경한 후 저장하는 코드입니다.

### Local Storage에서 불러온 데이터 파싱하기

local Storage에서 불러오는 데이터는 문자열이므로, 이를 자바스크립트 객체로 활용하기 위해서는 파싱해야 합니다.

```javascript
const loadedToDos = localStorage.getItem(TODO_LS);
const parseToDos = JSON.parse(loadedToDos); // JSON이란 'JavaScript Object Notation'의 줄임말로 데이터 전송시, 자바스크립트가 다룰 수 있도록 Object로 바꿔주는 기능을 의미.
```

### 요소생성

document.querySelector나 document.getElementById 등으로 DOM에 존재하는 요소를 가져올 수 있습니다. 이외에도 js에서 html요소를 생성할 수 있는 여러 방법이 존재합니다.

```javascript
const li = document.createElement("li");
const delBtn = document.createElement("button");
const span = document.createElement("span");
```

### Filter

```javascript
const cleanToDos = toDos.filter(function(toDo) {
  return toDo.id !== parseInt(li.id);
});
```

filter method는 각각의 item에 대해 같은 코드를 수행합니다. 최종적으로 결과값이 true인 아이템들을 array에 담아 return합니다.

=> toDo.id와 li.id가 다른 아이템들을 array에 담고 이를 cleanToDos에 반환합니다.

### Math Module

JavaScript에는 Math라는 모듈이 내장되어 있습니다.

```javascript
Math.random(); // 0과 1사이 숫자 생성.(실수 범위)
Math.random() * 3; // 0과 3사이 숫자 생성.(실수 범위)
Math.floor(Math.random() * 3); // 0과 3사이 정수 생성. (0포함 3 미포함) 소수점을 버림.
Math.ceil(Math.random() * 3); // 1과 4사이 정수 생성. (1포함 4 미포함) 소수점을 올림.
```

### API(Application Programming Interface)

API를 통해 다른 요소들은 배제한 채 오직 데이터만을 가져올 수 있습니다.

```javascript
const weatherContainer = document.querySelector(".js-weather");

const API_KEY = "2b461077b45a03601a15be3110b71617",
  COORDS = "coords";

function getWeather(lat, lon) {
  fetch(
    `https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=${API_KEY}&units=metric`
  )
    .then(function(response) {
      // then은 해당 API로부터 응답이 오면 then이후를 실행하겠다는 뜻.
      // 응답 Data 받음.
      // console.log(response.json());
      // 콘솔창을 보면 앱에 필요한 데이터는 pending 상태입니다. 따라서 then 과정을 한번 더 작성해 필요한 데이터를 가져옵니다.
      return response.json();
    })
    .then(function(json) {
      console.log(json);

      const location = json.name;
      const temp = Math.floor(json.main.temp);

      weatherContainer.innerText = `${location}동, ${temp}도 `;
    });
}

function saveCoords(coordsObj) {
  localStorage.setItem(COORDS, JSON.stringify(coordsObj));
}

function handleGeoSuccess(position) {
  //console.log(position);
  const lat = position.coords.latitude;
  const lon = position.coords.longitude;
  const coordsObj = {
    lat,
    lon
  };
  saveCoords(coordsObj);
  getWeather(lat, lon);
}
```
