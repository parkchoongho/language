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

