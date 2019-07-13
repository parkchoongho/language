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

<br>

### Add a box-shadow to a Card-like Element

`box-shadow` property는 요소에 하나 이상의 그림자를 적용할 수 있습니다. 

The `box-shadow`property takes values for `offset-x`(how far to push the shadow horizontally from the element), `offset-y`(how far to push the shadow vertically from the element), `blur-radius`, `spread-radius`and a color value, in that order. The `blur-radius`and `spread-radius`values are optional.

```css
box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
```

<br>

### Decrease the Opacity of an Element

`opacity` property는 CSS에서 요소의 transparency를 조정하는데 사용됩니다.

```pseudocode
A value of 1 is opaque, which isn't transparent at all.
A value of 0.5 is half see-through.
A value of 0 is completely transparent.
```

The value given will apply to the entire element, whether that's an image with some transparency, or the foreground and background colors for a block of text.

<br>

### Use the text-transform Property to Make Text Uppercase

 `text-transform` property는 text의 모습을 조정하는데 사용됩니다. 

It's a convenient way to make sure text on a webpage appears consistently, without having to change the text content of the actual HTML elements.

The following table shows how the different `text-transform`values change the example text "Transform me".

| Value        | Result                                                |
| :----------- | :---------------------------------------------------- |
| `lowercase`  | "transform me"                                        |
| `uppercase`  | "TRANSFORM ME"                                        |
| `capitalize` | "Transform Me"                                        |
| `initial`    | Use the default value                                 |
| `inherit`    | Use the `text-transform`value from the parent element |
| `none`       | **Default:** Use the original text                    |

```css
h4 {
    text-align: center;
    background-color: rgba(45, 45, 45, 0.1);
    padding: 10px;
    font-size: 27px;
    text-transform: uppercase;
}
```

<br>

### Set the line-height of Paragraphs

`line-height` property는 블록 각각의 줄에 존재하는 text의 높이를 조정할 수 있습니다. As the name suggests, it changes the amount of vertical space that each line of text gets.

```css
p {
    font-size: 16px;
    line-heightL 25px;
}
```

<br>

### Adjust the Hover State of an Anchor Tag

This challenge will touch on the usage of pseudo-classes. A pseudo-class is a keyword that can be added to selectors, in order to select a specific state of the element.

For example, the styling of an anchor tag can be changed for its hover state using the `:hover`pseudo-class selector. Here's the CSS to change the `color`of the anchor tag to red during its hover state:

```css
a:hover {
    color: red;
}
```

<br>

### Change an Element's Relative Position

CSS treats each HTML element as its own box, which is usually referred to as the `CSS Box Model`. Block-level items automatically start on a new line (think headings, paragraphs, and divs) while inline items sit within surrounding content (like images or spans). The default layout of elements in this way is called the `normal flow`of a document, but CSS offers the position property to override it.

When the position of an element is set to `relative`, it allows you to specify how CSS should move it *relative* to its current position in the normal flow of the page. It pairs with the CSS offset properties of `left`or `right`, and `top`or `bottom`. These say how many pixels, percentages, or ems to move the item *away* from where it is normally positioned. The following example moves the paragraph 10 pixels away from the bottom:

```css
p {
  position: relative;
  bottom: 10px;
}
```

Changing an element's position to relative does not remove it from the normal flow - other elements around it still behave as if that item were in its default position.

**Tip**: Positioning gives you a lot of flexibility and power over the visual layout of a page. It's good to remember that no matter the position of elements, the underlying HTML markup should be organized and make sense when read from top to bottom. This is how users with visual impairments (who rely on assistive devices like screen readers) access your content.

<br>

###  Move a Relatively Positioned Element with CSS Offsets

The CSS offsets of `top`or `bottom`, and `left`or `right`tell the browser how far to offset an item relative to where it would sit in the normal flow of the document. You're offsetting an element away from a given spot, which moves the element away from the referenced side (effectively, the opposite direction). As you saw in the last challenge, using the top offset moved the `h2`downwards. Likewise, using a left offset moves an item to the right.

```html
<head>
    <style>
        h2 {
            position: relative;
            left: 15px;
            bottom: 10px;
        }
    </style>
</head>
<body>
    <h1>On Being Well-Positioned</h1>
    <h2>Move me!</h2>
    <p>I still think the h2 is where it normally sits.</p>
</body>
```

### Lock an Element to its Parent with Absolute Positioning

The next option for the CSS `position`property is `absolute`, which locks the element in place relative to its parent container. Unlike the `relative`position, this removes the element from the normal flow of the document, so surrounding items ignore it. The CSS offset properties (top or bottom and left or right) are used to adjust the position.

One nuance with absolute positioning is that it will be locked relative to its closest *positioned* ancestor. If you forget to add a position rule to the parent item, (this is typically done using `position: relative;`), the browser will keep looking up the chain and ultimately default to the body tag.

```html
<style>
    #searchbar {
        position: absolute;
        top: 50px;
        right: 50px;
    }
    section {
        position: relative;
    }
</style>
<body>
    <h1>Welcome!</h1>
    <section>
        <form id="searchbar">
            <label for="search">Search:</label>
            <input type="search" id="search" name="search">
            <input type="submit" name="submit" value="Go!">
        </form>
    </section>
</body>
```

<br>

### Lock an Element to the Browser Window with Fixed Positioning

The next layout scheme that CSS offers is the `fixed`position, which is a type of absolute positioning that locks an element relative to the browser window. Similar to absolute positioning, it's used with the CSS offset properties and also removes the element from the normal flow of the document. Other items no longer "realize" where it is positioned, which may require some layout adjustments elsewhere.

One key difference between the `fixed`and `absolute`positions is that an element with a fixed position won't move when the user scrolls.

```html
<style>
    #navbar {
        position: fixed;
        top: 0px;
        left: 0px;
        width: 100%;
        background-color: #767676;
    }
    nav ul {
        margin: 0px;
        padding: 5px 0px 5px 30px;
    }
    nav li {
        display: inline;
        margin-right: 20px;
    }
    a {
        text-decoration: none;
    }
</style>
<body>
    <header>
        <h1>Welcome!</h1>
        <nav id="navbar">
            <ul>
                <li><a href="">Home</a></li>
                <li><a href="">Contact</a></li>
            </ul>
        </nav>
    </header>
    <p>I shift up when the #navbar is fixed to the browser window.</p>
</body>
```

The navigation bar in the code is labeled with an id of `navbar`. Change its `position`to `fixed`, and offset it 0 pixels from the `top`and 0 pixels from the `left`. Notice the (lack of) impact to the `h1`position, it hasn't been pushed down to accommodate the navigation bar and would need to be adjusted separately.

<br>

### Push Elements Left or Right with the float Property

The next positioning tool does not actually use `position`, but sets the `float`property of an element. Floating elements are removed from the normal flow of a document and pushed to either the `left`or `right`of their containing parent element. It's commonly used with the `width`property to specify how much horizontal space the floated element requires.

```html
<head>
    <style>
        #left {
            float: left;
            width: 50%;
        }
        #right {
            float: right;
            width: 40%;
        }
        aside, section {
            padding: 2px;
            background-color: #ccc;
        }
    </style>
</head>
<body>
    <header>
        <h1>Welcome!</h1>
    </header>
    <section id="left">
        <h2>Content</h2>
        <p>Good stuff</p>
    </section>
    <aside id="right">
        <h2>Sidebar</h2>
        <p>Links</p>
    </aside>
</body>
```

<br>

### Change the Position of Overlapping Elements with the z-index Property

When elements are positioned to overlap, the element coming later in the HTML markup will, by default, appear on the top of the other elements. However, the `z-index`property can specify the order of how elements are stacked on top of one another. It must be an integer (i.e. a whole number and not a decimal), and higher values for the `z-index`property of an element move it higher in the stack than those with lower values.

```html
<style>
    div {
        width: 60%;
        height: 200px;
        margin-top: 20px;
    }

    .first {
        background-color: red;
        position: absolute;
        z-index: 2;
    }
    .second {
        background-color: blue;
        position: absolute;
        left: 40px;
        top: 50px;
        z-index: 1;
    }
</style>

<div class="first"></div>
<div class="second"></div>
```

<br>

###  Center an Element Horizontally Using the margin Property

Another positioning technique is to center a block element horizontally. One way to do this is to set its `margin`to a value of auto.

This method works for images, too. Images are inline elements by default, but can be changed to block elements when you set the `display`property to block.

```html
<style>
    div {
        background-color: blue;
        height: 100px;
        width: 100px;
        margin: auto;
    }
</style>
<div></div>
```

<br>

### Learn about Complementary Colors

Color theory and its impact on design is a deep topic and only the basics are covered in the following challenges. On a website, color can draw attention to content, evoke emotions, or create visual harmony. Using different combinations of colors can really change the look of a website, and a lot of thought can go into picking a color palette that works with your content.

The color wheel is a useful tool to visualize how colors relate to each other - it's a circle where similar hues are neighbors and different hues are farther apart. When two colors are opposite each other on the wheel, they are called complementary colors. They have the characteristic that if they are combined, they "cancel" each other out and create a gray color. However, when placed side-by-side, these colors appear more vibrant and produce a strong visual contrast.

Some examples of complementary colors with their hex codes are:

```pseudocode
red (#FF0000) and cyan (#00FFFF)
green (#00FF00) and magenta (#FF00FF)
blue (#0000FF) and yellow (#FFFF00)
```

