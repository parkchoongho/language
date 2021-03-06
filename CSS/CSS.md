## 1. CSS 구성요소

**CSS**는 크게 2가지로 구성되어 있다.

### (1) Property

```css
property-name: value; 
/* 이름에 있어 중간 공백을 허용하지 않고 value 다음 마지막에 세미콜론(;)으로 마무리한다. */
```

### (2) Selector

위에 있는 **property**를 내 **h1** 태그에 연결시키고 싶다면?

```css
h1 {
  property-name: value;
  property-name: value;
  property-name: value;
  property-name: value;
  property-name: value;
  /* property를 원하는 만큼 selector에 적용할 수 있다. */
}
```

이렇게 작성하면 된다.

또 **selector**로 **ID** 또는 **Class**를 사용할 수 있는데 이 때는 그냥 태그와 표기법이 조금 달라진다.

```css
#id {
  property-name: value;
  property-name: value;
}

.class {
  property-name: value;
  property-name: value;
}
```

최종적으로 **css**는 이렇게 작성할 수 있다고 보면된다.

```css
selector (id, class, tag name) {
  property-name: value;
  property-name: value;
  property-name: value;
}
```

<br>

## 2. HTML과 CSS 연결하기

**CSS**를 **HTML**에서 사용하는 방법에는 2가지가 있다.

### (1) inline

```html
<head>
  <style>
    body {
      background-color: red;
    }
  </style>
</head>
<body></body>
```

**Tip:** 만약 프로젝트에서 배경이 빨간색인 파일이 여러개 필요하다면, 위 **style**코드를 각 **html** 파일에 모두 붙여넣어야 한다.

### (2) externel하게 연결

```html
<head>
  <link rel="stylesheet" href="style.css" />
</head>
<body></body>
```

```css
body {
  background-color: red;
}
```

이렇게 하면 `<link rel="stylesheet" href="style.css">` 로 각 **html** 파일에서 **css** 파일로 접근가능하다.

<br>

## 3. Box Model

### Box는 총 4가지 요소로 구성된다.

![boxmodel](https://user-images.githubusercontent.com/34790763/58922072-5bf13000-8774-11e9-8293-06051be265b4.png)

<br>

### (1) Content

**Content**는 말그대로 그 **Box**에 들어가는 내용물이다. 이미지, 영상, 텍스트 등등 다양한 형태의 파일을 가질 수 있다.

### (2) Padding

**Padding**은 **Content**와 **Border**사이의 간격을 의미한다.

### (3) Border

**Border**는 **Box**가 가지는 테두리를 나타낸다.

### (4) Margin

**Margin**은 **Border**로부터 바깥 쪽 요소와의 거리를 나타낸다.

### Padding Margin 단축키

```css
h1 {
  padding: 20px; /* 상하좌우 모두 padding을 20px만큼 준다. */
  padding: 20px 10px; /* 상하는 20px 좌우는 10px */
  padding: 20px 15px 10px 5px; /* 상부터 시작해서 상 우 하 좌 시계방향으로 적용된다. */
}
```

margin도 같은 방식으로 동작한다.

### Border

```css
h1 {
  border-width: 5px;
  border-color: blue;
  border-style: dashed; /* 점선을 의미 */
  border: 5px dashed blue; /* 이렇게 단축해서 표현 가능. */
}
```

<br>

## 4. Display

### (1) Block

옆에 어떤 요소도 허용하지 않을 때, **Block**을 사용한다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      .box {
        display: block;
        width: 200px;
        height: 200px;
        background-color: red;
        border: 2px solid black;
      }
    </style>
  </head>
  <body>
    <span class="box"></span>
    <span class="box"></span>
    <span class="box"></span>
  </body>
</html>
```

<img width="161" alt="block" src="https://user-images.githubusercontent.com/34790763/58922106-83e09380-8774-11e9-9d9e-67d40b2db628.PNG">

크기와 상관없이 옆에 다른 요소를 허용하지 않는 것을 **Block**이라 한다.

### (2) Inline-Block

**Inline-Block**은 옆에 다른 요소가 오는 것을 허용한다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      .box {
        display: inline-block;
        width: 200px;
        height: 200px;
        background-color: red;
        border: 2px solid black;
      }
    </style>
  </head>
  <body>
    <span class="box"></span>
    <span class="box"></span>
    <span class="box"></span>
  </body>
</html>
```

<img width="472" alt="inlineblock" src="https://user-images.githubusercontent.com/34790763/58922131-a1156200-8774-11e9-80fb-0d2d8916dd8b.PNG">

**Box**는 **Block**과 **Inline-Block**중 하나의 값을 가져야한다. (디폴트 값은 **Block**이다.)

### 3) Inline

**Inline**은 박스안의 모든 **Property** 설정값을 지운다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      .box {
        display: inline;
        width: 200px;
        height: 200px;
        background-color: red;
        border: 2px solid black;
      }
    </style>
  </head>
  <body>
    <span class="box">1</span>
    <span class="box">1</span>
    <span class="box">1</span>
  </body>
</html>
```

<img width="50" alt="inline" src="https://user-images.githubusercontent.com/34790763/58922140-ad99ba80-8774-11e9-90a9-f5e52aad5915.PNG">

**Inline**으로 **Display**를 설정하면 더 이상 **Block**으로 설정되지 않는다. 대신에 위 예시처럼 **Text**로 적용된다.

따라서 만약에 **Inline** 설정값을 유지하는 동시에 **Box**형태를 원한다면 **Inline-Block**을 **Display** 설정값으로 사용한다.

<br>

## 5. Position

```css
 body,
 html 
{
    height: 100%;
    margin: 0;
    padding: 0;
}
```

이렇게 설정하는 이유는 브라우저가 가지고 있는 디폴트 값을 상쇄시키기 위함이다. (브라우저마다 가지고 있는 CSS 값이 다르기 때문이다.)

### (1) Static

 **Static**은 요소가 그 자리에 계속 있다는 말이다. 모든 박스의 디폴트 값은 **Static**이다. Static이 지정된 요소는 document의 일반적인 흐름(normal flow)를 따라 배치된다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      body,
      html {
        height: 100%;
        margin: 0;
        padding: 0;
      }
      body {
        height: 400%;
        background-color: red;
      }
      .box {
        width: 300px;
        height: 300px;
        background-color: beige;
      }
    </style>
  </head>
  <body>
    <div class="box">
      <div class="box-child"></div>
    </div>
  </body>
</html>
```

### (2) Fixed

**Fixed**로 지정된 요소는 문서 흐름에 있어 제거되고 페이지 레이아웃에서 요소를 위한 공간이 형성되지 않는다. 대신, 스크린의 viewport를 기준으로 해서 위치가 정해지는데, 따라서 스크롤해도 움직이지 않는 고정자리를 가진다. **Fixed**는 항상 그 자리에 고정되어 브라우저에 나타난다.(스크롤해도 사라지지 않는다.) 포지션을 고정하고 상, 하, 좌, 우를 줄 수 있다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      body,
      html {
        height: 100%;
        margin: 0;
        padding: 0;
      }
      body {
        height: 400%;
        background-color: red;
      }
      #boxOne {
        width: 300px;
        height: 300px;
        background-color: beige;
        position: static;
      }
      #boxTwo {
        width: 300px;
        height: 300px;
        background-color: greenyellow;
        position: fixed;
        top: 10px;
      }
    </style>
  </head>
  <body>
    <div id="boxOne">
      <div class="box-child"></div>
    </div>
    <div id="boxTwo">
      <div class="box-child"></div>
    </div>
  </body>
</html>
```

### (3) Absolute, Relative

**Relative**로 지정된 요소는 document의 normal flow에 따라 배치된다. 그리고 요소 자신에 대한 상대적인 top, bottom, left, right 속성에 의한 좌표로 배치된다. (별도의 거리 속성을 주지 않는다면, static과 동일하게 작용한다.) 이때의 좌표는 다른 요소들의 위치에 영향을 주지 않는다. 페이지 레이아웃 상에서 요소에게 할당된 공간은 static과 동일하다.

**Absolute**로 지정된 요소는 문서 흐름에서 제외되고 페이지 레이아웃에서 요소를 위한 공간이 형성되지 않는다. 대신, 가장 가까운 위치에 있는 조상에 대해 상대적 위치에 배치된다. 조상이 없는 경우에는 초기 컨테이닝 블록을 기준으로 배치된다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      body,
      html {
        height: 100%;
        margin: 0;
        padding: 0;
      }
      body {
        height: 400%;
        background-color: red;
      }
       .abs-box {
        width: 400px;
        height: 400px;
        background-color: yellow;
      }
      .abs-child {
        width: 100px;
        height: 100px;
        background-color: green;
        position: absolute;
        right: 0;
      }
    </style>
  </head>
  <body>
    <div class="abs-box">
      <div class="abs-child"></div>
    </div>
  </body>
</html>
```

이렇게 하면 **abs-child** div가 맨 오른쪽으로 이동한 것을 볼 수있다. 왜냐하면 **abs-child** div가 **html** 상에서 **부모**에 해당하는 요소를 찾지 못했기 때문이다. 다시 말하면, **absolute** **position**이 설정되면 이 요소는 해당 요소와 관계가 있는 (**relative - 부모박스**) 요소를 찾게 되고 이에 따라 위치가 결정된다. 반대로 부모요소를 찾지 못했다면 **body**에 맞춰서 움직이게 된다. 밑에 코드를 보자.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      body,
      html {
        height: 100%;
        margin: 0;
        padding: 0;
      }
      body {
        height: 400%;
        background-color: red;
      }
      .abs-box {
        width: 400px;
        height: 400px;
        background-color: yellow;
        position: relative;
      }
      .abs-child {
        width: 100px;
        height: 100px;
        background-color: green;
        position: absolute;
        right: 10px;
        top: 10px;
      }
    </style>
  </head>
  <body>
    <div class="abs-box">
      <div class="abs-child"></div>
    </div>
  </body>
</html>
```

이렇게 관계를 만들어주면 **abs-child** div요소는 이제 그 상위의 부모 요소인 **abs-box**에 상대적으로 움직이게 된다.

참고 문헌: https://developer.mozilla.org/ko/docs/Web/CSS/position

<br>

## 6. Flex

### (1) 기존 display의 문제점

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      .box {
        background-color: red;
        width: 200px;
        height: 200px;
        display: inline-block;
      }
    </style>
  </head>
  <body>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
    <div class="box"></div>
  </body>
</html>
```

많은 박스를 갖게 되면 요소들이 자동으로 밑으로 넘어간다. 

**Margin**도 각기 달라지고 (마지막과 첫 **Margin**) 또 가운데 정렬, 모바일 호환 문제 등등 여러 방면에서 기존 **Display**는 문제점을 가지고 있다. 

### (2) Flex Box 모델

flexbox라 불리는 모델은 Flex Box Module은 flexbox내 아이템간 공간 배분과 강력한 정렬 기능을 제공하기 위한 1차원 레이아웃 모델이다. flexbox를 1차원적이라 함은, 레이아웃을 다룰 때 한 번에 하나의 차원(행 또는 열)만을 다룬다는 의미이다. 이는 행과 열을 동시에 고려하는 CSS Grid Layout과는 대조적인 부분이다.

### (3) Flex 사용법

Flex는 부모 클래스를 만들고 그 안에 적용하고 싶은 박스들을 생성한다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      .father {
        display: flex;
      }
      .box {
        background-color: red;
        width: 200px;
        height: 200px;
      }
    </style>
  </head>
  <body>
    <div class="father">
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
    </div>
  </body>
</html>
```

Flex는 Chlidren 박스에 적용하지 않는다. 오직 부모 클래스에만 적용한다. 또, flex를 설정하면 box 클래스에 inline-block으로 display속성을 설정하지 않아도 inline-block처럼 작용한다.

**justify-content, align-items**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      body,
      html {
        height: 100%;
      }
      .father {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100%;
      }
      .box {
        background-color: red;
        width: 200px;
        height: 200px;
      }
    </style>
  </head>
  <body>
    <div class="father">
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
    </div>
  </body>
</html>
```

- justify-content: 가로로 아이템 정렬하는 것을 제어
- align-items: 세로로 아이템을 정렬하는 것을 제어

=> **둘다 디폴트 값이다. flex-direction으로 가로, 세로를 변경할 수 있다.**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      body,
      html {
        height: 100%;
      }
      .father {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100%;
        flex-direction: column;
      }
      .box {
        background-color: red;
        width: 200px;
        height: 200px;
      }
    </style>
  </head>
  <body>
    <div class="father">
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
    </div>
  </body>
</html>

```

=> **flex-direction을 column으로 설정(디폴트 값이 row)하면 justify-content가 세로 align-items가 가로가 된다.**

박스가 많아지면 flex가 어떻게 되는지 보자.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      body,
      html {
        height: 100%;
      }
      .father {
        display: flex;
        justify-content: center;
        align-items: flex-start;
        height: 100%;
      }
      .box {
        background-color: red;
        width: 200px;
        height: 200px;
        border: 1px solid black;
      }
    </style>
  </head>
  <body>
    <div class="father">
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
    </div>
  </body>
</html>
```

box의 property가 width: 200px로 설정되어 있어 inline-block은 밑으로 넘어갔지만 flex는 box의 width를 자동으로 줄여준다.

<br>

<img width="944" alt="flex" src="https://user-images.githubusercontent.com/34790763/59353387-d49c5180-8d5d-11e9-9138-4ca9da59edda.PNG">

브라우저의 크기를 늘리거나 줄이면 그 화면에 맞게 box들이 자신들의 크기를 조정한다.

그런데 만약에 박스를 간격에 맞게 밑으로 내리고 싶다면 어떻게 해야할까?

<br>

**flex-wrap**

flex-wrap property를 wrap으로 설정하면 box가 기존에 설정된 값을 유지하게 되고 화면을 넘어가는 box들을 밑으로 내려보낸다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      body,
      html {
        height: 100%;
      }
      .father {
        display: flex;
        justify-content: space-around;
        align-items: flex-start;
        height: 100%;
        flex-wrap: wrap;
      }
      .box {
        background-color: red;
        width: 200px;
        height: 200px;
        border: 1px solid black;
      }
    </style>
  </head>
  <body>
    <div class="father">
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
      <div class="box"></div>
    </div>
  </body>
</html>
```

flex-wrap property가 wrap으로 설정되어 있기 때문에 화면 구성이 이렇게 된다.

(디폴트 값은 no wrap이다.)

<img width="938" alt="flex-wrap" src="https://user-images.githubusercontent.com/34790763/59353467-ff86a580-8d5d-11e9-8b18-6d88f5bb98ba.PNG">

<br>

## 7. Pseudo-Selector (가상 셀렉터)

**가상 셀럭터란, 셀렉터인데 element가 아닌 것을 뜻한다.** 

**(태그이름이나 class id를 사용하지 않고 선택하는 방법)**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      input[type="submit"] {
        background-color: red;
      }
      input[type="password"] {
        background-color: blue;
      }
      input {
        border: 1px solid yellow;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="box"></div>
      <div class="box"></div>
      <div class="box">
        <input type="password" />
        <input type="submit" />
      </div>
    </div>
  </body>
</html>
```

이렇게 속성 값으로 접근하는 것을 가상 셀럭터라고 한다.

#### 여러 가상셀렉터

```css
.box:last-child {
        background-color: green;
}
```

=> 모든 box class를 가진 요소중에 마지막 요소 배경을 green으로 설정하라.

```css
.box:first-child {
        background-color: green;
}
```

=> 모든 boxclass를 가진 요소중에 첫번째 요소 배경을 green으로 설정하라.

```css
.box:nth-child(2) {
        background-color: green;
}
```

=> 모든 box class를 가진 요소중에 두번째 요소 배경을 green으로 설정하라.

#### 직계

```css
.container > .box {
        background-color: yellow;
}
```

direct child 직계라고 하고 바로 밑에 있는 child에게만 해당된다.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <style>
      .container > .box {
        background-color: yellow;
      }
      .box {
        display: block;
        height: 200px;
        border: 1px solid black;
      }
      .child {
        background-color: aqua;
        width: 50%;
        height: 100%;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="box">
        <div class="child"></div>
      </div>
      <div class="box"></div>
      <div class="box"></div>
    </div>
  </body>
</html>
```

<img width="942" alt="directchild" src="https://user-images.githubusercontent.com/34790763/59353505-16c59300-8d5e-11e9-94ef-bc7bd7838f0c.PNG">

**이렇게 화면이 구성되는 이유는 child class 박스는 container class의 직계가 아니기에 영향을 받지 않기 때문이다.**

<br>

## 8. CSS States

### Active Focus Visited Hover 이렇게 총 4개의 State가 존재한다.

브라우저 요소 검사 창에서 확인 가능

- **Hover**: 해당 요소에 먼가가 올라오면(hover) 실행.

```css
.box {
    background-color: rebeccapurple;
    font-size: 40px;
}

.box:hover {
    background-color: aquamarine;
}
```

- **Active**: 해당 요소를 클릭하면 실행.

```css
.box {
    background-color: rebeccapurple;
    font-size: 40px;
}

.box:active {
    background-color: aquamarine;
}
```

- **Focus**: 해당요소에 focus(해당요소가 선택된 상태)가 되면 실행.

```css
.box {
    background-color: rebeccapurple;
    font-size: 40px;
}

.box:focus {
    background-color: aquamarine;
}
```

- **Visited**: 해당 요소를 클릭하면 해당 링크가 보여지는 것.

```css
.box:visited {
    background-color: green;
}
```

<br>

## 9. Transitions

**CSS Transition**은 CSS 속성을 변경할 때 애니메이션 속도를 조절하는 방법을 나타냅니다. 속성 변경이 바로 적용되는 대신, 그 변화가 일정기간에 걸쳐 일어나도록 할 수 있습니다. 웹에서 여러가지 동작 -이동/ 변경 등등- 을 보여주는 효과가 트랜지션이다. 두 상태 사이의 트랜지션을 포함하는 애니메이션을 암묵적 트랜지션이라 칭하기도 하는데, 이는 시작과 종료 사이의 상태를 브라우저가 암묵적으로 정의하기 때문입니다.

```css
.box {
    background-color: green;
    color: white;
}
.box:hover {
    background-color: blueviolet;
}
```

이렇게 hover를 적용하면 변화하는 과정(Transitions)이 없다. 그 사이에 아무런 애니매이션이 없게된다.

```css
.box {
    background-color: green;
    color: white;
    transition: background-color 2s ease-in;
}
.box:hover {
    background-color: blueviolet;
}
```

코드에는 이렇게 적용시키면 된다.

```css
.box {
    background-color: green;
    color: white;
    transition: all 2s ease-in;
}
.box:hover {
    background-color: blueviolet;
}
```

1개 이상의 설정값에 적용하고 싶다면 위 코드처럼 transition 애니메이션 이름에 all이라 적으면 된다.

Transition은 어떤 State가 바뀔 떄 적용되는 것이다. (State에는 **hover, active, focus**, visited등이 있다.)  =>  굵게 칠해진 3개에 효과적으로 적용된다.

참고 문헌: https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions

<br>

## 10. Transformations

**Transform**은 좌표공간을 변형함으로써 문서 normal flow를 방해하지 않고 콘텐츠의 형태와 위치를 바꿔줍니다.

```css
.box {
    width: 500px;
    height: 500px;
    background-color: red;
    transform: rotate(20deg);
}
```

[CSS Transform Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS/transform)

다양한 Transform을 시도해 볼수 있는 링크

```css
.box {
    width: 500px;
    height: 500px;
    background-color: red;
    transition: transform 2s ease-in-out;
}
.box:hover {
    transform: rotate(1turn);
}
```

Transition과 연결한 예시

<br>

## 11. Animations

**CSS Animation**은 한 요소에 적용되는 CSS 스타일을 다른 CSS 스타일로 전환시켜줍니다. 애니메이션은 애니메니션을 나타내는 CSS 스타일과 애니메이션의 중간 상태를 나타내는 키프레임들로 이루어집니다.

#### 어떠한 효과를 State를 줄 필요 없이 계속 발생하길 원한다면 어떻게 할까?

keyframes은 css로 하여금 animation이 생성되었음을 알려준다.

```css
.box {
    width: 500px;
    height: 500px;
    background-color: red;
    animation: 1.5s scaleAndRotateSquare infinite ease-in-out;
}
@keyframes scaleAndRotateSquare {
    from {
        transform: none;
    }
    to {
        transform: rotate(1turn) scale(0.5, 0.5);
    }
}
```

이렇게  from to로(단계가 2가지만 있는 상황) 어떤 상태에서 다른 상태로 변하는 것을 표현할 수 있다.

```css
.box {
    width: 500px;
    height: 500px;
    background-color: red;
    animation: 1.5s scaleAndRotateSquare infinite ease-in-out;
}
@keyframes scaleAndRotateSquare {
    0% {
        transform: none;
    }
    50% {
        transform: rotate(1turn) scale(0.5, 0.5);
    }
    100% {
        transform: none;
    }
}
```

%로 여러 상태를 동시에 표현하는 것도 가능하다.

<br>

## 12. Media Queries

#### 디바이스의 종류마다 필요한 화면의 크기가 다르다. 브라우저가 필요한 크기에 따라 제어하는 것이 필요할 때 사용하는 것이 Media Query다.

```css
body {
    background-color: green;
}
@media screen and (min-width: 320px) and (max-width: 640px) {
    body {
        background-color: blueviolet;
    }
}
```

반응형 웹디자인에 유용하다.(모바일-데스크탑 환셩에 따라 반응하기 때문에)

[Using media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)

Media Query 관련 링크