## Applied Visual Design



### Create Visual Balance Using the text-align Property

`text-align` property를 활용하여 글자를 align할 수 있습니다. 

`text-align: justify;`: 마지막 줄을 제외하고 줄 box의 왼쪽과 오른쪽을 맞춰줍니다.

`text-align: center;`: 중앙으로 정렬시킵니다.

`text-align: right;`: 오른쪽으로 정렬시킵니다.

`text-align: left;`: 왼쪽으로 정렬시킵니다.(default)

<br>

### Adjust the Width of an Element Using the width Property

`width` property를 활용해 요소의 width를 정할 수 있습니다. Value는 상대적인 길이단위(em), 절대적인 길이단위(px) 또는 부모요소에 대한 비율 값으로도 가능합니다.

```css
img {
    width: 220px;
}
```

<br>

### Adjust the Height of an Element Using the height Property

`height` property를 활용해 요소의 height를 정할 수 있습니다. `height`은 `width`와 매우 흡사합니다.

```css
img {
    height: 20px;
}
```

<br>

### Use the strong Tag to Make Text Bold

`strong` tag를 활용하면 text를 두껍게 만들 수 있습니다. 이는 종종 글자에 관심을 두게하고 싶거나 중요하다고 알릴 때 사용됩니다. strong 태그를 통해, 브라우저는 그 요소에  `font-weight: bold;` CSS와 같은 효과를 줍니다.

```html
<p>Google was founded by Larry Page and Sergey Brin while they were Ph.D. students at <strong>Stanford University</strong>.</p>
```

<br>

### Use the u Tag to Underline Text

text에 밑줄을 주기위해, `u` 태그를 사용할 수 있습니다. 특정 부분이 중요하다고 강조하고 싶을 때 `u` 태그를 사용합니다. `u` 태그를 통해, 브라우저는 그 요소에 `text-decoration: underline;`CSS와 같은 효과를 줍니다.

```html
<p>Google was founded by Larry Page and Sergey Brin while they were <u>Ph.D. students</u> at <strong>Stanford University</strong>.</p>
```

Tip: `a` link tag와 혼동할 수 있으므로 `u` 태그의 사용은 지양하는 것이 좋습니다. `a` 태그도 밑줄 형태의 default 값을 가지고 있습니다.

<br>

### Use the em Tag to Italicize Text

text를 강조하기위해 `em` 태그를 사용할 수 있습니다. 이 태그는 text를 italicized하게 보여줍니다. (브라우저가 `font-style: italic;` CSS와 같은 효과를 줍니다.  )

```html
<p> <em>Google was founded by Larry Page and Sergey Brin while they were <u>Ph.D. students</u> at <strong>Stanford University</strong>.</em> </p>
```

<br>

### Use the s Tag to Strikethrough Text

text를 strikethrough하고 싶으면 (취소선 긋기), `s` 태그를 사용해 할 수 있습니다. 이것은 그 text가 더이상 유효하지 않다는 것을 보여줍니다. `s` 태그를 통해, 브라우저는 그 요소에 `text-decoration: line-through;`CSS와 같은 효과를 줍니다.

```html
<h4><s>Google</s>Alphabet</h4>
```

<br>

### Create a Horizontal Line Using the hr Element

`hr` 태그를 활용해 태그를 포함하는 부모 요소에 해당하는 수평선을 만들 수 있습니다. 이는 보통 주제를 바꾸거나 content를 시각적으로 그룹별로 구분할 때 사용됩니다.

```html
<h4><s>Google</s>Alphabet</h4>
<hr>
<p><em>Google was founded by Larry Page and Sergey Brin while they were <u>Ph.D. students</u> at <strong>Stanford University</strong>.</em></p>
```

**Tip**: `hr`은 self-closing tag이므로 따로 closing tag가 필요하지 않습니다.

<br>

### Adjust the background-color Property of Text

Instead of adjusting your overall background or the color of the text to make the foreground easily readable, you can add a `background-color`to the element holding the text you want to emphasize. This challenge uses `rgba()`instead of `hex`codes or normal `rgb()`.

```pseudocode
rgba stands for:
  r = red
  g = green
  b = blue
  a = alpha/level of opacity
```

The RGB values can range from 0 to 255. The alpha value can range from 1, which is fully opaque or a solid color, to 0, which is fully transparent or clear. `rgba()`is great to use in this case, as it allows you to adjust the opacity. This means you don't have to completely block out the background.

You'll use `background-color: rgba(45, 45, 45, 0.1)`for this challenge. It produces a dark gray color that is nearly transparent given the low opacity value of 0.1.

```css
h4 {
    text-align: center;
    padding: 10px;
    background-color: rgba(45, 45, 45, 0.1);
}
```

<br>

### Adjust the Size of a Header Versus a Paragraph Tag

The font size of header tags (`h1`through `h6`) should generally be larger than the font size of paragraph tags. This makes it easier for the user to visually understand the layout and level of importance of everything on the page. You use the `font-size`property to adjust the size of the text in an element.

```css
h4 {
    text-align: center;
    background-color: rgba(45, 45, 45, 0.1);
    padding: 10px;
    font-size: 27px;
}
```

