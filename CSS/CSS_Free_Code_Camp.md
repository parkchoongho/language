# CSS

### Change the Color of Text

텍스트의 색깔을 바꿀 수 있습니다. `style` 속성을 변경해 이를 바꿀 수 있습니다. 요소의 텍스트 색깔에 영향을 주는 것은 `color` style property입니다. 

```html
<h2 style="color: blue;">CatPhotoApp</h2>
```

`style`안 쪽 선언은 `;`으로 끝납니다.

<br>

### Use CSS Selectors to Style Elements

CSS안에는 수백개의 CSS `properties`  가 존재합니다. `<h2 style="color: red">CatPhotoApp</h2>` 처럼 CSS를 입력하는 방법을 `inline CSS` 라 합니다.

이러한 방법보다 더 효율적으로 CSS 를 적용하는 방법이 존재합니다.

```html
<style>
</style>
```

`style` block 안에 `CSS selector` 를 만들 수 있습니다. `h2` 텍스트 색깔을 빨간 색으로 바꾸고 싶으면 이렇게 코드를 작성할 수 있다.

```html
<style>
    h2 {color: red;} <!-- 각각의 스타일 rule은 semi colon으로 끝난다. -->
</style>
```

<br>

### Use a CSS Class to Style an Element

class는 계속 재사용되고 html에서 활용할 수 있는 style 입니다. 클래스 CSS style 적용은 이렇게 됩니다.

```html
<style>
    .blue-text {
        color: blue;
    }
</style>
```

HTML 요소에 이렇게 class를 적용할 수 있습니다.

```html
<h2 class="blue-text">CatPhotoApp</h2>
```

Tip: CSS `style` 에서 class 이름은 `.` 으로 시작하는 것을 기억하자. & Class는 HTML 여러 요소에 적용할 수 있습니다.

<br>

### Change the Font Size of an Element

`font-size` CSS property를 통해 글자크기를 제어할 수 있습니다.

```css
h1 {
    font-size: 30px;
}
```

 <br>

### Set the Font Family of an Element

`font-family` property로 어떤 폰트를 사용할지 설정할 수 있습니다.

```css
h2 {
    font-family: sans-serif;
}
```

이렇게 하면 `h2` 태그는 sans-serif 폰트를 사용하게 됩니다.

<br>

### Import a Google Font

이미 OS 시스템에서지원하는 폰트외에도, custom한 웹 폰트를 웹 사이트에서 사용할 수 있다. 인터넷에 다양한 웹 폰트 소스들이 존재하는데, 그 중 우리는 Google Fonts 라이브러리를 사용할 예정이다. Google Fonts 라이브러리는 무료로, font의 URL을 통해 참조하고 이를 CSS에 적용할 수 있다.

Google Fonts를 적용하기 위해서, URL을 Google Fonts 라이브러리에서 복사하고 이를 HTML 파일에 붙여넣기 합니다.

```html
<link href="https://fonts.googleapis.com/css?family=Lobster" rel="stylesheet" type="text/css">
```

이제 아래코드에서 `Lobster`를 CSS FAMILY_NAME에 입력함으로써  `Lobster` 폰트를 사용할 수 있습니다.

`font-family: FAMILY_NAME, GENERIC_NAME;`

GENERIC_NAME은 optional 합니다. FAMILY_NAME 폰트가 적용되지 않았을시, 그 다음 이 폰트를 적용합니다. Family name은 case-sensitive하며 단어 사이에 공백이 있을 경우 quotes로 감싸야합니다.

`font-family: "Open Sans"`

<br>

### Specify How Fonts Should Degrade

모든 브라우저에서 사용가능하 default font들이 있습니다. 이 Generic font들은 `monospace`, `serif` 그리고 `sans-serif` 폰트를 포함합니다. 만약 한 포트를 사용할 수 없으면그 다음 포트를 부를 수 있습니다. (이걸 영어로는 degrade라 합니다.  => Tell the browser to "degrade" to another font)

```css
p {
    font-family: Helvetica, sans-serif;
}
```

Generic 폰트들은 case-sensitive하지 않습니다. 또한 quotes로 감쌀 필요도 없습니다.(CSS keyword이기 때문입니다.)

<br>

### Size Your Images

CSS는 요소의 width를 제어할 수 있는 `width` property를 가지고 있습니다. 이미지의 width를 정하기 위해 `px` 를 사용합니다. (font에서도 사용)

```html
<style>
    .larger-image {
        width: 500px;
    }
</style>
```

<br>

### Add Borders Around Your Elements

CSS border는 `style`, `color` 그리고 `width` 같은 properties를 가집니다. 

```html
<style>
    .thin-red-border {
        border-color: red;
        border-width: 5px;
        border-style: solid;
    }
</style>
```

`border-radius` property를 활용해 모서리 부분을 둥그렇게 만들 수 있습니다. `border-radius` 값을 pixels 또는 percentage로 줄 수 있습니다.

```html
<style>
    .thin-red-border {
        border-color: red;
        border-width: 5px;
        border-style: solid;
        border-radius: 10px;
    }

    .thick-green-border {
        border-color: green;
        border-width: 10px;
        border-style: solid;
        border-radius: 50%;
    }
</style>
```

Tip: 한 개의 요소에는 클래스 이름간에 공백을 둠으로써 여러 클래스를 적용할 수 있습니다.

```html
<img class="class1 class2">
```

<br>

### Give a Background Color to a div Element

`background-color` property에 색깔을 설정해 배경색을 줄 수 있습니다.

```css
.green-background {
    background-color: green;
}
```

<br>

### Set the id of an Element

class 처럼, 각각의 HTML 요소는 `id`를 가질 수 있습니다. `id`는 unique 해야합니다. 브라우저가 이를 강제하지는 않지만, unique하게 사용하는 것이 좋습니다. 따라서 같은 이름의 `id`를 서로 다른 요소에 주지 않아야합니다.

```html
<h2 id="cat-photo-app">
```

<br>

### Use an id Attribute to Style an Element

class 처럼 또한, `id`에도 CSS를 활용해 style을 입힐 수 있습니다. 하지만 `id` 는 오직 하나의 요소에만 적용이 가능합니다. 그리고 `id`는 higher specificity (importance)를 가지므로, 만약 한 요소에 `id`와 class가 모두 적용되어 있고 두개가 충돌되는 style을 가지고 있다면, `id`의 스타일이 적용됩니다. `id`에는 아래와 같은 방법으로 style을 적용합니다. `#`을 이름 앞에 붙혀  `id`를  참조합니다.

```css
#cat-photo-element {
    background-color: green;
}
```

<br>

### Adjust the Padding of an Element

모든 html 요소는 반드시 직사각형 모양을 띕니다. 세개의 중요한 요소가 HTML 요소 주변 space를 컨트롤합니다: `padding`, `margin` and `border`.

`padding`은 요소 content와 `border` 사이의 공간을 제어합니다. 

 (사진)

여기서 빨간 box가 파란 box 보다 더 많은 padding을 가지고 있습니다. 파란 박스의 padding 값을 늘리면 border와 text사이의 거리(`padding`)가 늘어납니다.

<br>

### Adjust the Margin of an Element

`margin` 은 요소의 `border`와 그 요소를 감싸고 있는 요소사이의 거리를 나타냅니다.

 (사진)

이 그림에서 빨간box가 파란 box보다 더 큰 `margin` 을 가진다는 것을 알 수 있습니다. 파란 box의 `margin` 크기를 늘리면 그 border와 이를 감싸고 있는 요소 사이의 거리(`margin`)가 늘어납니다.

<br>

### Add a Negative Margin to an Element

`margin` 에 음수값을 주면, 그 요소는 점점 커지게 됩니다.

 (사진)

<br>

### Add Different Padding to Each Side of an Element

각 방향 마다 다른 `padding` 값을 주어  요소를 customize할 수 있습니다. 각각의 방향은 `padding-top`, `padding-right`, `padding-bottom`, and `padding-left` properties입니다.

```css
.blue-box {
    background-color: blue;
    color: #fff;
    padding-top:40px;
    padding-left:40px;
    padding-bottom: 20px;
    padding-right:20px;
}
```

 (사진)

`padding-top`, `padding-right`, `padding-bottom`, and `padding-left` properties 각각에 값을 주는 대신 이를 한줄로 나타낼 수 있습니다.

```css
.blue-box {
    background-color: blue;
    color: #fff;
   padding: 10px 20px 10px 20px;
}
```

4개의 값은 시계 방향으로 적용됩니다: top, right, bottom, left.

<br>

### Add Different Margins to Each Side of an Element

`margin` 또한 각 방향마다 값을 줄 수 있으며 각 방향은 `margin-top`, `margin-right`, `margin-bottom`, and `margin-left` properties입니다.

```css
.blue-box {
    background-color: blue;
    color: #fff;
    margin-top: 40px;
    margin-left:40px;
    margin-bottom: 20px;
    margin-right: 20px;
}
```

 (사진)

`margin-top`, `margin-right`, `margin-bottom`, and `margin-left` properties 각각에 값을 주는 대신 이를 한줄에 나타낼 수 있습니다.

```css
.blue-box {
    background-color: blue;
    color: #fff;
    margin: 10px 20px 10px 20px;
}
```

4개의 값은 시계방향으로 적용됩니다: top, right, bottom, left.

<br>

### Use Attribute Selectors to Style Elements

`[attr=value]`attribute selector를 활용해 요소에 style을 입힐 수 있습니다. 

```css
[type='radio'] {
    margin: 20px 0px 20px 0px;
}
```

위 코드는 `type` 이 `radio` 인 모든 요소의 margin 값을 코드대로 설정합니다.

<br>

### Understand Absolute versus Relative Units

지금까지 px 단위를 사용해왔습니다. px말고도 CSS는 다양한 단위를 가지고 있습니다. 가장 흔히 사용되는 단위는 absolute와 relative입니다. absolute unit은 물리적인 단위와 연관되어 있습니다. 예를 들어, `in` 과 `mm` 은 각각 inches와 millimeters를 뜻합니다. Absolute 단위는 화면상에서의 실제 크기등을 나타냅니다. 

Relative한 단위 (예를 들어, `em` 또는 `rem`) 들은 화면에 따라 다른 단위를 나타냅니다. 예를 들어, `em` 은 요소의 font 크기를 결정할 수 도 있습니다. 만일 `font-size: 1.5em;` 이렇게 설정했다면, 상위 요소(부모요소)의 1.5배 크기의 font 크기를 가집니다. 

```css
.red-box {
    background-color: red;
    margin: 20px 40px 20px 40px;
    padding: 1.5em;
}
```

Tip: There are several relative unit options that are tied to the size of the viewport. They are covered in the Responsive Web Design Principles section.

<br>

###  Inherit Styles from the Body Element

모든 요소들은 `body` 태그의 스타일을 inherit합니다.

```html
<style>
    body {
        background-color: black;
        color: green;
        font-family: monospace;
    }

</style>

<h1>Hello World</h1>
```

`h1` 태그는 초록색, monospace 글씨체를 가지게 됩니다.

<br>

### Prioritize One Style Over Another

종종 HTML 요소들은 충돌되는 여러개의 스타일을 받게 됩니다. 예를 들어, `h1` 태그는 green이면서 동시에 pink 색일 수 없습니다. 

```html
<style>
    body {
        background-color: black;
        font-family: monospace;
        color: green;
    }

    .pink-text{
        color:pink;
    }
</style>
<h1 class="pink-text">Hello World!</h1>
```

이렇게 하면 `.pink-text`에 설정해 놓은 pink가 `body`에 설정해 놓은 green을 override합니다.

```html
<style>
    body {
        background-color: black;
        font-family: monospace;
        color: green;
    }


    .pink-text {
        color: pink;
    }
    .blue-text{
        color: blue;
    }

</style>
<h1 class="pink-text blue-text">Hello World!</h1>
```

.blue-text에 설정된 blue값이 .pink-text에 설정된 pink 값을 override합니다.(뒤에 선언된 값이 앞에 선언된 값을 override합니다.) `style` 안에서 선언된 값들은 순서가 중요합니다.

Tip: HTML 요소 상에서 선언되는 순서는 아무 상관이 없습니다.

`<h1 class="pink-text blue-text">Hello World!</h1>`와 `<h1 class="blue-text pink-text">Hello World!</h1>` 는 완전히 똑같습니다.

<br>

### Override Class Declarations by Styling ID Attributes

브라우저는 CSS를 위에서부터 아래로 읽어내려갑니다. 따라서 스타일 충돌이 일어날 때, 브라우저는 가장 나중에 선언된 스타일을 적용합니다. 

그에 반해 `id`는 어디에 선언되든, 항상 클래스보다 우선됩니다.

```html
<style>
    #orange-text{
        color: orange;
    }
    .blue-text {
        color: blue;
    }

</style>
<h1 id="orange-text" class="blue-text">Hello World!</h1>
```

이렇게 코드를 짜면 h1의 text 색깔은 orange가 됩니다.

Tip: It doesn't matter whether you declare this CSS above or below pink-text class, since id attribute will always take precedence.	

<br>

### Override Class Declarations with Inline Styles

`inline style`은 id, class에 우선되어 나타납니다.

```html
<style>
    #orange-text {
        color: orange;
    }
    .pink-text {
        color: pink;
    }
    .blue-text {
        color: blue;
    }
</style>
<h1 style="color:white;" id="orange-text" class="pink-text blue-text">Hello World!</h1>
```

위 코드에서 h1 text 색깔은 하얀색으로 나타납니다.

<br>

### Override All Other Styles by using Important

CSS 라이브러리(부트스트랩 같은)를 사용하면 우연찮게 그 전에 작성해 놓은 CSS를 override하는 경우가 있습니다. 따라서 이 경우, 다시 되돌리기 위해 `!important`를 사용할 수 있습니다.

```html
<style>
    #orange-text {
        color: orange;
    }
    .pink-text {
        color: pink !important;
    }
    .blue-text {
        color: blue;
    }
</style>
<h1 id="orange-text" class="pink-text blue-text" style="color: white">Hello World!</h1>
```

이렇게 하면 h1의 색깔은 pink 색으로 나타납니다.

<br>

### Use Hex Code for Specific Colors

CSS에서는 hexadecimal code (줄여서 `hex code`) 를 통해 색깔을 나타냅니다. `Hexadeciaml`(or `hex`) 는 16진법을 기반으로 하는 수를 의미합니다. 0~9, A~F를 사용하여 하나의 자릿수를 표현합니다. (0~F는 0~15를 의미합니다.)

CSS에서 우리는 6,자리의 hexadecimal 숫자를 사용합니다. 2자리씩 끊어서 각각이 red(R), green(G), blue(B)를 나타냅니다.

```css
body{
    color: #000000;
}
```

From these three pure colors (red, green, and blue), we can vary the amounts of each to create over 16 million other colors!

The digit `0`is the lowest number in hex code, and represents a complete absence of color.

The digit `F`is the highest number in hex code, and represents the maximum possible brightness.

<br>

### Use Abbreviated Hex Code

color red의 경우 `#FF0000`으로 나타냅니다. 이것을 `#F00`으로 줄여서 나타낼 수 있습니다.(여기서 각각 1자리 숫자씩 red, green, blue를 나타냅니다.) 이렇게 함으로써 가능한 색깔을 약 4000개를 줄일 수 있습니다.

```css
body{
    color: #F00
}
```

<br>

### Use RGB values to Color Elements

CSS에서 색깔을 나타내는 또 다른 방법은 `RGB`입니다. RGB에서 검은색은 `rgb(0, 0, 0)` 으로 나타내고 하얀색은 `rgb(255, 255, 255)`로 나타냅니다. `RGB`안에 있는 세개의 숫자는 `hex code`에서 사용되는 숫자 2자리와 동일하게 대응합니다.

```css
body {
    background-color: rgb(255, 165, 0) == #FFA500
}
```

<br>

### Use CSS Variables to change several elements at once

CSS *Variables* 은 많은 CSS properties를 하나의 value만 바꿔서 바꿀 수 있는 매우 powerful한 방법입니다.

CSS Variable을 생성하기 위해, `two dashes` 를 `name` 앞에 붙이고 `value`를 할당합니다. 

```css
--penguin-skin: gray;
```

`--penguin-skin` 변수를 만들고 여기에 `gray`라는 값을 할당했습니다. 이제 어떤 요소를 gray로 만들기 위해 이 변수를 가져가 CSS에서 사용할 수 있습니다.

<br>

### Use a custom CSS Variable

변수를 생성하고 이를 CSS의 다른 properties에 할당해서 사용할 수 있습니다. (by referencing the name you gave it.)

```css
background: var(--penguin-skin);
```

이렇게 하면 `--penguin-skin` 변수의 value 값을 background 값으로 가지게 됩니다.

```css
.penguin-top {
    top: 10%;
    left: 25%;

    /* change code below */
    background: var(--penguin-skin);
    /* change code above */

    width: 50%;
    height: 45%;
    border-radius: 70% 70% 60% 60%;
}
```

<br>

### Attach a Fallback value to a CSS Variable

CSS에서 브라우저가 주어진 변수가 유효하지 않을 때를 대비해서 가져올 `fallback` value를 줄 수 있습니다.

Tip: This fallback is not used to increase browser compatibilty, and it will not work on IE browsers. Rather, it is used so that the browser has a color to display if it cannot find your variable.

```css
background: var(--penguin-skin, black);
```

fallback을 줌으로써 디버깅할 때 도움을 받을 수 있습니다.

<br>

### Improve Compatibility with Browser Fallbacks

When working with CSS you will likely run into browser compatibility issues at some point. This is why it's important to provide browser fallbacks to avoid potential problems.

When your browser parses the CSS of a webpage, it ignores any properties that it doesn't recognize or support. For example, if you use a CSS variable to assign a background color on a site, Internet Explorer will ignore the background color because it does not support CSS variables. In that case, the browser will use whatever value it has for that property. If it can't find any other value set for that property, it will revert to the default value, which is typically not ideal.

This means that if you do want to provide a browser fallback, it's as easy as providing another more widely supported value immediately before your declaration. That way an older browser will have something to fall back on, while a newer browser will just interpret whatever declaration comes later in the cascade.

<br>

###  Cascading CSS variables

변수를 만들면 변수가 적용된 요소 안에 nested 되어있는 요소에만 적용할 수 있습니다. 이러한 것을 `cascading`이라 합니다. 

이러한 특징 때문에, CSS 변수들은  *:root* 요소 안에 정의되어집니다. `:root` 요소는 HTML document 전체를 담고 있는 container입니다. (`html` 요소가 `body` 요소를 담고 있는 것과 같은 의미입니다.) 변수들을 `:root` 안에 생성하면, 이 변수들은 웹페이지 전체에서 사용가능해집니다.

```css
:root {

    /* add code below */
    --penguin-belly: pink;
    /* add code above */
}

body {
    background: var(--penguin-belly, #c6faf1);
}
```

<br>

### Use a media query to change a variable

CSS Variables는 media queries를 사용하는 방식을 간편하게 만들어 줍니다. (For instance, when your screen is smaller or larger than your media query break point, you can change the value of a variable, and it will apply its style wherever it is used.)

```css
:root {
    --penguin-size: 300px;
    --penguin-skin: gray;
    --penguin-belly: white;
    --penguin-beak: orange;
}

@media (max-width: 350px) {
    :root {

        /* add code below */
        --penguin-size: 200px;
        --penguin-skin: black;
        /* add code above */

    }
}
```

