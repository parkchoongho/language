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

