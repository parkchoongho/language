# 1. CSS 구성요소

**CSS**는 크게 2가지로 구성되어 있다.



### (1) Property

```css
property-name: value; /* 이름에 있어 중간 공백을 허용하지 않고 value 다음에 마지막으로 세미콜론(;)으로 마무리한다. */
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
  /*property를 원하는 만큼 selector에 적용할 수 있다.*/
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





# 2. HTML과 CSS 연결하기

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

이 방법이 좋지 않은 이유는 만일 어떤 프로젝트에서 배경이 빨간색인 파일이 여러개 필요하다고 할 때, 위 **style**코드를 각 **html** 파일에 계속해서 붙여넣어야 하기 때문이다.



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

이렇게 하면 <link rel="stylesheet" href="style.css"> 로 각 **html** 파일에서 **css** 파일로 접근할 수 있다.





# 3. Box Model

### Box는 총 4가지 요소로 구성된다.

![boxmodel](https://user-images.githubusercontent.com/34790763/58922072-5bf13000-8774-11e9-8293-06051be265b4.png)



### (1) Content

**Content**는 말그대로 그 **Box**에 들어가는 내용물이다. 이미지, 영상, 텍스트 등등 다양한 형태의 파일을 가질 수 있다.



### (2) Padding

**Padding**은 **Content**와 **Border**사이의 간격을 의미한다.



### (3) Border

**Border**는 **Box**가 가지는 테두리를 나타낸다.



### (4) Margin

**Margin**은 **Border**로부터 바깥 쪽 요소와의 거리를 나타낸다.**(확실한가?)**



### Padding Margin 단축키

```css
h1 {
  padding: 20px; /* 상하좌우 모두 padding을 20px만큼 준다. */
  padding: 20px 10px; /* 상하는 20px 좌우는 10px */
  padding: 20px 15px 10px 5px; /* 상부터 시작해서 상 우 하 좌 시계방향으로 적용된다. */
}
```

margin에도 똑같이 적용된다.



### Border

```css
h1 {
  border-width: 5px;
  border-color: blue;
  border-style: dashed; /* 점선을 의미 */
  border: 5px dashed blue; /* 이렇게 단축해서 표현할 수도 있다. */
}
```





# 4. Display



### (1) Block

Block은 옆에 아무것도 없을 때 **Block**이라고 한다.

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

이렇게 크기와 상관없이 옆으로 다른요소를 허용하지 않는 것을 **Block**이라 칭한다.



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

따라서 만약에 **Inline** 설정값을 유지하는 동시에 **Box**형태를 원한다면 **Inline-Block**을 **Display** 설정값으로 사용하면된다.



# 5. Position

```css
 body,
 html 
{
    height: 100%;
    margin: 0;
    padding: 0;
}
```

이걸 설정하는 이유는 브라우저가 가지고 있는 디폴트 값을 상쇄시키기 위함이다.



### Position은 4가지가 존재한다.



### (1) Static

 **Static** 요소를 거기두면 그 자리에 있을 것이라는 말이다. (# 먼 말이지?) 모든 박스의 디폴트 값은 **Static**이다.

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

**Fixed**는 항상 그 자리에 고정되어 브라우저에 나타난다.(스크롤해도 사라지지 않는다.) 포지션을 고정하고 상, 하, 좌, 우를 줄 수 있다.

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

어디에든 붙을 수 있다는 점에서 **Fixed**랑 비슷하다. 하지만, 스크롤해서 보이지는 않는다.

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





# 6. Flex



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

이렇게 많은 박스를 갖게 되면 자동으로 밑으로 넘어가게 된다. (이 많은 블록을 옆으로 붙게하고 싶어도 방법이 없음.)

이렇게 설정할시 **Margin**도 각가 달라진다. (마지막과 첫 **Margin**) 또, 가운데 정렬, 핸드폰과의 호환 등등 여러 부분에서 기존의 **Display**는 문제점을 가지고 있었다.

따라서 자동으로 완성되는 **Grid**가 필요!! 



### (2) Flex 사용법



Flex는 부모 클래스를 만들고 그 안에 적용하고 싶은 박스들을 만든다.

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

Flex를 사용할 때는 Chlidren 박스에 적용하지 않는다. 오직 부모 클래스에만 적용한다. 

이렇게 코드를 작성하면 box 클래스에 inline-block으로 display속성을 설정하지 않아도 inline-block처럼 적용된다.



#### justify-content, align-items

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

=> **이렇게 flex-direction을 column으로 설정(디폴트 값이 row)하면 justify-content가 세로 align-items가 가로가 된다.**



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

이렇게 설정하면 box width 200px로 인해 inline-block은 자동으로 밑으로 넘어갔지만 flex는 box의 width를 자동으로 줄여준다.



![](C:\Users\user\Desktop\Project\language\CSS\images\flex.PNG)

브라우저의 크기를 늘리거나 줄이면 그 화면에 맞게 box들이 자신들의 크기를 조정한다.

그런데 만약에 박스를 간격에 맞게 밑으로 내리고 싶다면 어떻게 해야할까?



#### flex-wrap

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

이렇게 코드를 작성하면 flex-wrap property가 wrap으로 설정되어 있기 때문에 화면 구성이 이렇게 된다.

(디폴트 값은 no wrap이다.)

![](C:\Users\user\Desktop\Project\language\CSS\images\flex-wrap.PNG)





# 7. Pseudo-Selector (가상 셀렉터)

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

모든 box class를 가진 요소중에 마지막 요소 배경을 green으로 설정하라.



```css
.box:first-child {
        background-color: green;
}
```

모든 boxclass를 가진 요소중에 첫번째 요소 배경을 green으로 설정하라.



```css
.box:nth-child(2) {
        background-color: green;
}
```

모든 box class를 가진 요소중에 두번째 요소 배경을 green으로 설정하라.



#### 직계

```css
.container > .box {
        background-color: yellow;
}
```

direct child 직계라고 하고 그 밑에 있는 child에게는 해당되지 않는다.



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

![](C:\Users\user\Desktop\Project\language\CSS\images\directchild.PNG)

**이렇게 화면이 구성되는데 왜냐하면 child class 박스는 container class의 직계가 아니기 때문에 영향을 받지 않기 때문이다.**





# 8. CSS States

#### Active Focus Visited Hover 이렇게 총 4개의 State가 존재한다.

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





# 9. Position

```css
 body,
 html 
{
    height: 100%;
    margin: 0;
    padding: 0;
}
```

이걸 설정하는 이유는 브라우저가 가지고 있는 디폴트 값을 상쇄시키기 위함이다

### Position은 4가지가 존재한다.



### (1) Static

 **Static** 요소를 거기두면 그 자리에 있을 것이라는 말이다. (# 먼 말이지?) 모든 박스의 디폴트 값은 **Static**이다.

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

**Fixed**는 항상 그 자리에 고정되어 브라우저에 나타난다.(스크롤해도 사라지지 않는다.) 포지션을 고정하고 상, 하, 좌, 우를 줄 수 있다.

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

어디에든 붙을 수 있다는 점에서 **Fixed**랑 비슷하다. 하지만, 스크롤해서 보이지는 않는다.

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





# 10. Transitions

#### 웹에서의 여러가지 동작 -이동/ 변경 등등- 을 멋지게 보여주는 효과가 트랜지션이다.



```css
.box {
    background-color: green;
    color: white;
}
.box:hover {
    background-color: blueviolet;
}
```

이렇게 hover를 적용하면 변경할때 변화하는 모습(Transitions)효과가 없다. 그 사이에 아무런 애니매이션이 없게된다.



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





# 11. Transformations

#### HTML 문서 element들을 변경하여 모습이 변하는 효과

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





# 12. Animations

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





# 13. Media Queries

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