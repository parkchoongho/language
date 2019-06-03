# 1. Why JS?

JavaScript는 웹에서 쓰이는 유일한 프로그래밍 언어

Backend에는 많은 옵션들이 존재(Python, Ruby, 하스켈, ASP,...etc)

But, Frontend는 바로 JavaScript로 해야한다. 



# 2. ES5, ES6 ?

ECMAScript의 준말이며 일종의 Specification이다.

**(Specification이 머지?)**

=> JavaScript는 중앙 집중화가 잘 되어있어 누군가 업데이트를 하면 모든 브라우저에서 작동하게 된다. 이렇게 JavaScript는 일종의 체계 메뉴얼을 갖추고 있는데 이를 두고 Specification이라 한다. 이를 다른발로 ECMAScript라 하는 것이다. 각각의 브라우저 마다 이 Specification을 받아 다르게 해석한다. 

뒤에 붙는 숫자는 ECMAScript의 버전 업데이트를 말하는 것이다. 



# 3. Vanilla JavaScript

Vanilla JavaScript는 JavaScript의 일종으로 라이브러리가 없는 JavaScript를 이야기한다.

(브라우저를 통해 제공된 JavaScript라 보면 편하다.)

JavaScript는 프로그래머가 나쁜 코드를 작성하는 것을 허용한다. 

각각의 Instruction은 다른 줄에 존재한다. (이런 한줄에 존재하는 것을 **Expression**이라 부른다.) <br>Expression은 한줄에 존재해야한다. 한 Expression이 끝났다는 것은 **';'**을 마지막에 붙혀 표현한다.

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



### Data Types

