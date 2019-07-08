# HTML5

### Introduction to HTML5 Elements

HTML5 는 좀 더 descriptive한 HTML 태그들을 제공합니다. 이 태그들에는 `header, footer, nav, video, article, section`  과 같은 태그들이 존재합니다. 이 태그들은 HTML을 더 의미있게 해주고 SEO(Search Engine Optimization)과 접근성에 있어 도움을 줍니다. `main` 태그는 검색엔진이나 다른 개발자들이 웹페이지의 주요 내용을 찾는 걸 도와주는 역할을 합니다.

<br>

### Add Images to Your Website

모든 `img` 요소들은 **반드시** `alt`  속성을 가지고 있어야합니다. `alt` 속성을 나타내는 text는 screen reader에게 접근성을 높여주고, 이미지 업로드가 실패했을시 화면에 나타납니다. 

Tip: If the image is purely decorative, using an empty `alt`attribute is a best practice. (무슨 뜻이지?)

필요한 경우를 제외하면 `alt` 속성이 특수문자를 포함하지 않는 것이 좋습니다.

```html
<img src="https://www.your-image-source.com/your-image.jpg" alt="Author standing on a beach with two thumbs up.">
```

<br>

### Link to External Pages with Anchor Elements

웹페이지 외부 정보에 접근하는데 `anchor` tag를 사용할 수 있습니다. `anchor` 태그는 `href` 라 불리는 웹주소 목적지가 필요합니다.

```html
<a href="https://freecodecamp.org">this links to freecodecamp.org</a>
```

브라우저는 **"this links to freecodecamp.org"** 를 보여줄 것이고 이 부분을 클릭하면 **https://www.freecodecamp.org** 링크로 이동하게 됩니다.

<br>

###  Link to Internal Sections of a Page with Anchor Elements

`anchor` 태그를 사용하면 웹 페이지내 다른 section으로 넘어가는게 가능합니다. Internal link를 만들기 위해서는 `href` 특성에 `#`(Hash Symbol) 을 할당합니다. 그리고 그 요소의 `id` 값을 넣어 그 요소로 넘어갈 수 있습니다. `id` 는 그 웹 페이지내 유일한 값을 가지는 특성입니다.

```html
<a href="#contacts-header">Contacts</a>
...
<h2 id="contacts-header">Contacts</h2>
```

유저가 Contacts 링크를 클릭하면, 그 유저는 Contacts header 요소로 넘어가게 됩니다.

`target` anchor 태그가 가지는 특성으로 링크를 어디에 열지를 결정합니다. `"_blank"` 값을 가지면 링크를 새로운 탭에 엽니다.

<br>

### Make Dead Links Using the Hash Symbol

종종 `a` 태그 링크를 어디에 걸어야할지 알기전에 `a` 태그를 사용할 때가 있습니다. 이를 dead link라 합니다. `Javascript`를 사용해 링크를 제어하고 싶을 때 이 방법은 매우 유용합니다. 

```html
<p>Click here to view more <a href="#" target="_blank">cat photos</a>.</p>
```

<br>

### Turn an Image into a Link

`a` 태그안에 이미지를 넣어서 링크를 걸 수도 있습니다.

```html
<a href="#"><img src="https://bit.ly/fcc-running-cats" alt="Three kittens running towards the camera."></a>
```

<br>

### Create a Bulleted Unordered List

HTML은 `undordered list`를 만들 수 있는 태그를 가지고 있습니다.

```html
<ul>
  <li>milk</li>
  <li>cheese</li>
</ul>
```

이렇게 하면 bullet point 스타일의 "milk"와 "cheese" 리스트를 만들 수 있습니다.

<br>

### Create an Ordered List

HTML에서는 또한 `ordered list`를 만드는 것도 가능합니다.

```html
<ol>
  <li>Garfield</li>
  <li>Sylvester</li>
</ol>
```

 이렇게 하면 번호가 매겨진 리스트를 만들 수 있습니다.

<br>

### Create a Text Field

`input`태그는 웹 사용자로부터 입력을 받을 수 있는 편리한 방법입니다.

```html
<input type="text">
```

`input` 태그는 self-closing합니다.

Placeholder text는 사용자가 입력전에 `input` 태그안에 보여질 내용입니다.

```html
<input type="text" placeholder="this is placeholder text">
```

<br>

###  Create a Form Element

server에 데이터를 보낼 때 web form을 만들어 보낼 수 있습니다. `form` 태그에 특정 action을 설정해 이러한 작업을 할 수 있습니다. 

```html
<form action="/url-where-you-want-to-submit-form-data"></form>
```

`form` 태그에 `submit` 버튼을 달 수 있습니다. 그 버튼을 클릭하면 `action` 특성에 설정해둔 URL로 데이터를 전송하게 됩니다. 

```html
<form action="/url-where-you-want-to-submit-form-data">
    <button type="submit">this button submits the form</button>
</form>
```

`required` 특성을 활용하면 유저에게 form을 채우기 전까지는 데이터를 보내지 못하게 할 수 있습니다.

```html
<input type="text" required>
```

<br>

### Create a Set of Radio Buttons

`radio buttons`를 사용해 여러 대답 중 하나만 선택하는 질문을 유저에게 할 수 있습니다. `radio buttons` 도 `input` 태그의 한 종류입니다. 

각각의 버튼들은 `label` 태그안으로 들어올 수 있습니다. `input` 태그를 `label` 태그로 감싸면 자동적으로 `input` 태그와 `label` 태그를 연관지어줍니다. 

모든 `radio buttons`들은 하나의 그룹안에서는 같은 `name` 특성을 가져야합니다. 같은 그룹안에서는 하나의 버튼을 클릭하면 자동으로 다른 옵션들은 deselected됩니다. 이렇게 함으로써 유저가 하나의 옵션만을 선택할 수 있게끔 합니다.

```html
<label> 
  <input type="radio" name="indoor-outdoor">Indoor 
</label>
```

`for` 특성을 `label` 태그에 설정해 놓는 것이 좋은 습관입니다. 

It is considered best practice to set a `for`attribute on the `label`element, with a value that matches the value of the `id`attribute of the `input`element. This allows assistive technologies to create a linked relationship between the label and the child `input`element. For example:

```html
<label for="indoor"> 
  <input id="indoor" type="radio" name="indoor-outdoor">Indoor 
</label>
```

```html
<label for="indoor">
    <input type="radio" name="indoor-outdoor" id="indoor">Indoor
</label>
<label for="outdoor">
    <input type="radio" name="indoor-outdoor" id="outdoor">Outdoor
</label>
```

<br>

### Create a Set of Checkboxes

Forms는 한개 이상의 답을 얻어올때 `checkboxes`를 사용합니다. Checkboxes는 `input`의 한 종류입니다. 각각의 checkbox는 자신의 `label` 태그안에 nested될 수 있습니다. `input` 태그를 `label` 태그로 감쌈으로서 check box input과 label 태그를 연관 시킬 수 있습니다.

모든 연관된 checkbox들은 다 같은 `name` 속성을 가져야 합니다. `label` 태그에 `for` 속성을 통해 명시적으로 `input`과 `label`의 관계를 보여주는 것이 좋습니다. (`input`의 id 속성과 `label`의 for 속성 연관 짓기)

```html
<label for="loving"><input id="loving" type="checkbox" name="personality"> Loving</label>
```

`checked` 속성을 통해 특정 checkbox가 선택되어 있는 것처럼 설정할 수 있습니다.

```html
<input type="radio" name="test-name" checked>
```

<br>

### Nest Many Elements within a Single div Element

`div` 태그는 다른 태그들을 포함하기 위한 목적을 가진 태그입니다. `div` 태그는 non-self-closing 태그로써 `<div>` 로 연후에는 반드시 `</div>` 로 닫아주어야 합니다.

```html
<div>
    <p>Things cats love:</p>
    <ul>
        <li>cat nip</li>
        <li>laser pointers</li>
        <li>lasagna</li>
    </ul>
    <p>Top 3 things cats hate:</p>
    <ol>
        <li>flea treatment</li>
        <li>thunder</li>
        <li>other cats</li>
    </ol>
</div>
```

<br>

### Declare the Doctype of an HTML Document

html 문서를 작성할시, 이 문서가 어떤 버전의 HTML 페이지인지 브라우저에게 알려주어야 합니다. HTML은 계속 업데이트 되고 있습니다. 대부분의 메인 브라우저들은 가장 최신의 HTML 버전 (HTML 5)을 지원하고 있습니다. 

`<!DOCTYPE...>` 을 html 파일 첫줄에 입력함으로써 브라우저에게 이 파일의 html 버전을 알릴 수 있습니다.   (`...` 부분은 HTML 버전을 입력하는 부분입니다.  HTML5의 경우 `<!DOCTYPE html>` 입니다.) !와 DOCTYPE(반드시 대문자로 입력)은 중요하며 특히 오래된 브라우저에게 중요합니다. 뒤에 `html` 부분은 case sensitive하지 않습니다. 

그 다음, HTML code의 다른 부분은 `html` 태그안으로 들어와야합니다. `<html>` 태그는 `<!DOCTYPE html>` 바로 밑에 줄에 오고 `</html>` 은 파일 마지막 줄에 오게 됩니다.

```html
<!DOCTYPE html>
<html>
  <!-- Your HTML code goes here -->
</html>
```

<br>

### Define the Head and Body of an HTML Document

`html` 태그안에 `head`, `body`와 같은 다른 요소를 포함시킬 수 있습니다. 만든 페이지 관련된 모든 정보 markup들은 `head` 태그안에 들어갑니다. 그리고 유저에게 보여지는 content markup은 `body` 태그안에 들어갑니다. 

`link`, `meta`, `title` and `style` 과 같은 Metadata 요소들은 `head` 태그안에 들어갑니다.

```html
<!DOCTYPE html>
<html>
    <head>
        <!-- metadata elements -->
    </head>
    <body>
        <!-- page contents -->
    </body>
</html>
```

