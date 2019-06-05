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

![](C:\Users\user\Desktop\Project\language\CSS\images\boxmodel.png)

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

![](C:\Users\user\Desktop\Project\language\CSS\images\block.PNG)

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

![](C:\Users\user\Desktop\Project\language\CSS\images\inlineblock.PNG)

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

![](C:\Users\user\Desktop\Project\language\CSS\images\inline.PNG)

**Inline**으로 **Display**를 설정하면 더 이상 **Block**으로 설정되지 않는다. 대신에 위 예시처럼 **Text**로 적용된다.

따라서 만약에 **Inline** 설정값을 유지하는 동시에 **Box**형태를 원한다면 **Inline-Block**을 **Display** 설정값으로 사용하면된다.
