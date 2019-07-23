## Introduction to the CSS Flexbox Challenges

  A website's User Interface ("UI") has two components. First, there are the visual elements, such as colors, fonts, and images. Second, there is the placement or positioning of those elements. In Responsive Web Design, a UI layout must accommodate many different browsers and devices accessing the content.

CSS3 introduced Flexible Boxes, or flexbox, to create page layouts for a dynamic UI. It is a layout mode that arranges elements in a predictable way for different screen sizes and browsers. While somewhat new, all popular modern browsers support flexbox. This section covers how to use flexbox and the different layout options it offers.

<br>

<br>

### Use display: flex to Position Two Boxes

This section uses alternating challenge styles to show how to use CSS to position elements in a flexible way. First, a challenge will explain theory, then a practical challenge using a simple tweet component will apply the flexbox concept.

Placing the CSS property `display: flex;`on an element allows you to use other flex properties to build a responsive page.

```html
<style>
    #box-container {
        height: 500px;
        display: flex;
    }

    #box-1 {
        background-color: dodgerblue;
        width: 50%;
        height: 50%;

    }

    #box-2 {
        background-color: orangered;
        width: 50%;
        height: 50%;

    }
</style>
<div id="box-container">
    <div id="box-1"></div>
    <div id="box-2"></div>
</div>
```

<br>

### Add Flex Superpowers to the Tweet Embed

To the right is the tweet embed that will be used as the practical example. Some of the elements would look better with a different layout. The last challenge demonstrated `display: flex`. Here you'll add it to several components in the tweet embed to start adjusting their positioning.

```html
<style>
    body {
        font-family: Arial, sans-serif;
    }
    header {
        display: flex;
    }
    header .profile-thumbnail {
        width: 50px;
        height: 50px;
        border-radius: 4px;
    }
    header .profile-name {
        display: flex;
        margin-left: 10px;
    }
    header .follow-btn {
        display: flex;
        margin: 0 0 0 auto;
    }
    header .follow-btn button {
        border: 0;
        border-radius: 3px;
        padding: 5px;
    }
    header h3, header h4 {
        display: flex;
        margin: 0;
    }
    #inner p {
        margin-bottom: 10px;
        font-size: 20px;
    }
    #inner hr {
        margin: 20px 0;
        border-style: solid;
        opacity: 0.1;
    }
    footer {
        display: flex;
    }
    footer .stats {
        display: flex;
        font-size: 15px;
    }
    footer .stats strong {
        font-size: 18px;
    }
    footer .stats .likes {
        margin-left: 10px;
    }
    footer .cta {
        margin-left: auto;
    }
    footer .cta button {
        border: 0;
        background: transparent;
    }
</style>
<header>
    <img src="https://pbs.twimg.com/profile_images/378800000147359764/54dc9a5c34e912f34db8662d53d16a39_400x400.png" alt="Quincy Larson's profile picture" class="profile-thumbnail">
    <div class="profile-name">
        <h3>Quincy Larson</h3>
        <h4>@ossia</h4>
    </div>
    <div class="follow-btn">
        <button>Follow</button>
    </div>
</header>
<div id="inner">
    <p>I meet so many people who are in search of that one trick that will help them work smart. Even if you work smart, you still have to work hard.</p>
    <span class="date">1:32 PM - 12 Jan 2018</span>
    <hr>
</div>
<footer>
    <div class="stats">
        <div class="Retweets">
            <strong>107</strong> Retweets
        </div>
        <div class="likes">
            <strong>431</strong> Likes
        </div>
    </div>
    <div class="cta">
        <button class="share-btn">Share</button>
        <button class="retweet-btn">Retweet</button>
        <button class="like-btn">Like</button>
    </div>
</footer>
```

<br>

### Use the flex-direction Property to Make a Row

Adding `display: flex`to an element turns it into a flex container. This makes it possible to align any children of that element into rows or columns. You do this by adding the `flex-direction`property to the parent item and setting it to row or column. Creating a row will align the children horizontally, and creating a column will align the children vertically.

Other options for `flex-direction`are row-reverse and column-reverse.

**Tip**: The default value for the `flex-direction`property is row.

```html
<style>
    #box-container {
        display: flex;
        height: 500px;
        flex-direction: row-reverse;
    }
    #box-1 {
        background-color: dodgerblue;
        width: 50%;
        height: 50%;
    }

    #box-2 {
        background-color: orangered;
        width: 50%;
        height: 50%;
    }
</style>

<div id="box-container">
    <div id="box-1"></div>
    <div id="box-2"></div>
</div>
```

<br>

### Apply the flex-direction Property to Create Rows in the Tweet Embed

The `header`and `footer`in the tweet embed example have child items that could be arranged as rows using the `flex-direction`property. This tells CSS to align the children horizontally.

```html
<style>
    body {
        font-family: Arial, sans-serif;
    }
    header {
        display: flex;
        flex-direction: row;
    }
    header .profile-thumbnail {
        width: 50px;
        height: 50px;
        border-radius: 4px;
    }
    header .profile-name {
        display: flex;
        margin-left: 10px;
    }
    header .follow-btn {
        display: flex;
        margin: 0 0 0 auto;
    }
    header .follow-btn button {
        border: 0;
        border-radius: 3px;
        padding: 5px;
    }
    header h3, header h4 {
        display: flex;
        margin: 0;
    }
    #inner p {
        margin-bottom: 10px;
        font-size: 20px;
    }
    #inner hr {
        margin: 20px 0;
        border-style: solid;
        opacity: 0.1;
    }
    footer {
        display: flex;
        flex-direction: row;
    }
    footer .stats {
        display: flex;
        font-size: 15px;
    }
    footer .stats strong {
        font-size: 18px;
    }
    footer .stats .likes {
        margin-left: 10px;
    }
    footer .cta {
        margin-left: auto;
    }
    footer .cta button {
        border: 0;
        background: transparent;
    }
</style>
<header>
    <img src="https://pbs.twimg.com/profile_images/378800000147359764/54dc9a5c34e912f34db8662d53d16a39_400x400.png" alt="Quincy Larson's profile picture" class="profile-thumbnail">
    <div class="profile-name">
        <h3>Quincy Larson</h3>
        <h4>@ossia</h4>
    </div>
    <div class="follow-btn">
        <button>Follow</button>
    </div>
</header>
<div id="inner">
    <p>I meet so many people who are in search of that one trick that will help them work smart. Even if you work smart, you still have to work hard.</p>
    <span class="date">1:32 PM - 12 Jan 2018</span>
    <hr>
</div>
<footer>
    <div class="stats">
        <div class="Retweets">
            <strong>107</strong> Retweets
        </div>
        <div class="likes">
            <strong>431</strong> Likes
        </div>
    </div>
    <div class="cta">
        <button class="share-btn">Share</button>
        <button class="retweet-btn">Retweet</button>
        <button class="like-btn">Like</button>
    </div>
</footer>
```

<br>

### Use the flex-direction Property to Make a Column

The last two challenges used the `flex-direction`property set to row. This property can also create a column by vertically stacking the children of a flex container.

```html
<style>
    #box-container {
        display: flex;
        height: 500px;
        flex-direction: column;
    }
    #box-1 {
        background-color: dodgerblue;
        width: 50%;
        height: 50%;
    }

    #box-2 {
        background-color: orangered;
        width: 50%;
        height: 50%;
    }
</style>

<div id="box-container">
    <div id="box-1"></div>
    <div id="box-2"></div>
</div>
```

<br>

### Apply the flex-direction Property to Create a Column in the Tweet Embed

The tweet embed `header`and `footer`used the `flex-direction`property earlier with a row value. Similarly, the items inside the `.profile-name`element would work well stacked as a column.

```html
<style>
    body {
        font-family: Arial, sans-serif;
    }
    header, footer {
        display: flex;
        flex-direction: row;
    }
    header .profile-thumbnail {
        width: 50px;
        height: 50px;
        border-radius: 4px;
    }
    header .profile-name {
        display: flex;
        flex-direction: column;
        margin-left: 10px;
    }
    header .follow-btn {
        display: flex;
        margin: 0 0 0 auto;
    }
    header .follow-btn button {
        border: 0;
        border-radius: 3px;
        padding: 5px;
    }
    header h3, header h4 {
        display: flex;
        margin: 0;
    }
    #inner p {
        margin-bottom: 10px;
        font-size: 20px;
    }
    #inner hr {
        margin: 20px 0;
        border-style: solid;
        opacity: 0.1;
    }
    footer .stats {
        display: flex;
        font-size: 15px;
    }
    footer .stats strong {
        font-size: 18px;
    }
    footer .stats .likes {
        margin-left: 10px;
    }
    footer .cta {
        margin-left: auto;
    }
    footer .cta button {
        border: 0;
        background: transparent;
    }
</style>
<header>
    <img src="https://pbs.twimg.com/profile_images/378800000147359764/54dc9a5c34e912f34db8662d53d16a39_400x400.png" alt="Quincy Larson's profile picture" class="profile-thumbnail">
    <div class="profile-name">
        <h3>Quincy Larson</h3>
        <h4>@ossia</h4>
    </div>
    <div class="follow-btn">
        <button>Follow</button>
    </div>
</header>
<div id="inner">
    <p>I meet so many people who are in search of that one trick that will help them work smart. Even if you work smart, you still have to work hard.</p>
    <span class="date">1:32 PM - 12 Jan 2018</span>
    <hr>
</div>
<footer>
    <div class="stats">
        <div class="Retweets">
            <strong>107</strong> Retweets
        </div>
        <div class="likes">
            <strong>431</strong> Likes
        </div>
    </div>
    <div class="cta">
        <button class="share-btn">Share</button>
        <button class="retweet-btn">Retweet</button>
        <button class="like-btn">Like</button>
    </div>
</footer>
```

<br>

### Align Elements Using the justify-content Property

Sometimes the flex items within a flex container do not fill all the space in the container. It is common to want to tell CSS how to align and space out the flex items a certain way. Fortunately, the `justify-content`property has several options to do this. But first, there is some important terminology to understand before reviewing those options.

[Here is a useful image showing a row to illustrate the concepts below.](https://www.w3.org/TR/css-flexbox-1/images/flex-direction-terms.svg)

Recall that setting a flex container as a row places the flex items side-by-side from left-to-right. A flex container set as a column places the flex items in a vertical stack from top-to-bottom. For each, the direction the flex items are arranged is called the **main axis**. For a row, this is a horizontal line that cuts through each item. And for a column, the main axis is a vertical line through the items.

There are several options for how to space the flex items along the line that is the main axis. One of the most commonly used is `justify-content: center;`, which aligns all the flex items to the center inside the flex container. Others options include:

- `flex-start`: aligns items to the start of the flex container. For a row, this pushes the items to the left of the container. For a column, this pushes the items to the top of the container.
- `flex-end`: aligns items to the end of the flex container. For a row, this pushes the items to the right of the container. For a column, this pushes the items to the bottom of the container.
- `space-between`: aligns items to the center of the main axis, with extra space placed between the items. The first and last items are pushed to the very edge of the flex container. For example, in a row the first item is against the left side of the container, the last item is against the right side of the container, then the other items between them are spaced evenly.
- `space-around`: similar to `space-between`but the first and last items are not locked to the edges of the container, the space is distributed around all the items

```html
<style>
    #box-container {
        background: gray;
        display: flex;
        height: 500px;
        justify-content: center;
    }
    #box-1 {
        background-color: dodgerblue;
        width: 25%;
        height: 100%;
    }

    #box-2 {
        background-color: orangered;
        width: 25%;
        height: 100%;
    }
</style>

<div id="box-container">
    <div id="box-1"></div>
    <div id="box-2"></div>
</div>
```

**Bonus**: Try the other options for the `justify-content`property in the code editor to see their differences. But note that a value of center is the only one that will pass this challenge.

<br>

### Use the justify-content Property in the Tweet Embed

The last challenge showed an example of the `justify-content`property. For the tweet embed, this property can be applied to align the items in the `.profile-name`element.

```html
<style>
    body {
        font-family: Arial, sans-serif;
    }
    header, footer {
        display: flex;
        flex-direction: row;
    }
    header .profile-thumbnail {
        width: 50px;
        height: 50px;
        border-radius: 4px;
    }
    header .profile-name {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        margin-left: 10px;
    }
    header .follow-btn {
        display: flex;
        margin: 0 0 0 auto;
    }
    header .follow-btn button {
        border: 0;
        border-radius: 3px;
        padding: 5px;
    }
    header h3, header h4 {
        display: flex;
        margin: 0;
    }
    #inner p {
        margin-bottom: 10px;
        font-size: 20px;
    }
    #inner hr {
        margin: 20px 0;
        border-style: solid;
        opacity: 0.1;
    }
    footer .stats {
        display: flex;
        font-size: 15px;
    }
    footer .stats strong {
        font-size: 18px;
    }
    footer .stats .likes {
        margin-left: 10px;
    }
    footer .cta {
        margin-left: auto;
    }
    footer .cta button {
        border: 0;
        background: transparent;
    }
</style>
<header>
    <img src="https://pbs.twimg.com/profile_images/378800000147359764/54dc9a5c34e912f34db8662d53d16a39_400x400.png" alt="Quincy Larson's profile picture" class="profile-thumbnail">
    <div class="profile-name">
        <h3>Quincy Larson</h3>
        <h4>@ossia</h4>
    </div>
    <div class="follow-btn">
        <button>Follow</button>
    </div>
</header>
<div id="inner">
    <p>I meet so many people who are in search of that one trick that will help them work smart. Even if you work smart, you still have to work hard.</p>
    <span class="date">1:32 PM - 12 Jan 2018</span>
    <hr>
</div>
<footer>
    <div class="stats">
        <div class="Retweets">
            <strong>107</strong> Retweets
        </div>
        <div class="likes">
            <strong>431</strong> Likes
        </div>
    </div>
    <div class="cta">
        <button class="share-btn">Share</button>
        <button class="retweet-btn">Retweet</button>
        <button class="like-btn">Like</button>
    </div>
</footer>
```

<br>

###  Align Elements Using the align-items Property

The `align-items`property is similar to `justify-content`. Recall that the `justify-content`property aligned flex items along the main axis. For rows, the main axis is a horizontal line and for columns it is a vertical line.

Flex containers also have a **cross axis** which is the opposite of the main axis. For rows, the cross axis is vertical and for columns, the cross axis is horizontal.

CSS offers the `align-items`property to align flex items along the cross axis. For a row, it tells CSS how to push the items in the entire row up or down within the container. And for a column, how to push all the items left or right within the container.

The different values available for `align-items`include:

- `flex-start`: aligns items to the start of the flex container. For rows, this aligns items to the top of the container. For columns, this aligns items to the left of the container.
- `flex-end`: aligns items to the end of the flex container. For rows, this aligns items to the bottom of the container. For columns, this aligns items to the right of the container.
- `center`: align items to the center. For rows, this vertically aligns items (equal space above and below the items). For columns, this horizontally aligns them (equal space to the left and right of the items).
- `stretch`: stretch the items to fill the flex container. For example, rows items are stretched to fill the flex container top-to-bottom.
- `baseline`: align items to their baselines. Baseline is a text concept, think of it as the line that the letters sit on.

```html
<style>
    #box-container {
        background: gray;
        display: flex;
        height: 500px;
        align-items: center;
    }
    #box-1 {
        background-color: dodgerblue;
        width: 200px;
        font-size: 24px;
    }

    #box-2 {
        background-color: orangered;
        width: 200px;
        font-size: 18px;
    }
</style>

<div id="box-container">
    <div id="box-1"><p>Hello</p></div>
    <div id="box-2"><p>Goodbye</p></div>
</div>
```

**Bonus**: Try the other options for the `align-items`property in the code editor to see their differences. But note that a value of center is the only one that will pass this challenge.

<br>

### Use the align-items Property in the Tweet Embed

The last challenge introduced the `align-items`property and gave an example. This property can be applied to a few tweet embed elements to align the flex items inside them.

```html
<style>
    body {
        font-family: Arial, sans-serif;
    }
    header, footer {
        display: flex;
        flex-direction: row;
    }
    header .profile-thumbnail {
        width: 50px;
        height: 50px;
        border-radius: 4px;
    }
    header .profile-name {
        display: flex;
        flex-direction: column;
        justify-content: center;
        margin-left: 10px;
    }
    header .follow-btn {
        display: flex;
        align-items: center;
        margin: 0 0 0 auto;
    }
    header .follow-btn button {
        border: 0;
        border-radius: 3px;
        padding: 5px;
    }
    header h3, header h4 {
        display: flex;

        margin: 0;
    }
    #inner p {
        margin-bottom: 10px;
        font-size: 20px;
    }
    #inner hr {
        margin: 20px 0;
        border-style: solid;
        opacity: 0.1;
    }
    footer .stats {
        display: flex;
        font-size: 15px;
    }
    footer .stats strong {
        font-size: 18px;
    }
    footer .stats .likes {
        margin-left: 10px;
    }
    footer .cta {
        margin-left: auto;
    }
    footer .cta button {
        border: 0;
        background: transparent;
    }
</style>
<header>
    <img src="https://pbs.twimg.com/profile_images/378800000147359764/54dc9a5c34e912f34db8662d53d16a39_400x400.png" alt="Quincy Larson's profile picture" class="profile-thumbnail">
    <div class="profile-name">
        <h3>Quincy Larson</h3>
        <h4>@ossia</h4>
    </div>
    <div class="follow-btn">
        <button>Follow</button>
    </div>
</header>
<div id="inner">
    <p>I meet so many people who are in search of that one trick that will help them work smart. Even if you work smart, you still have to work hard.</p>
    <span class="date">1:32 PM - 12 Jan 2018</span>
    <hr>
</div>
<footer>
    <div class="stats">
        <div class="Retweets">
            <strong>107</strong> Retweets
        </div>
        <div class="likes">
            <strong>431</strong> Likes
        </div>
    </div>
    <div class="cta">
        <button class="share-btn">Share</button>
        <button class="retweet-btn">Retweet</button>
        <button class="like-btn">Like</button>
    </div>
</footer>
```

<br>

### Use the flex-wrap Property to Wrap a Row or Column

CSS flexbox has a feature to split a flex item into multiple rows (or columns). By default, a flex container will fit all flex items together. For example, a row will all be on one line.

However, using the `flex-wrap`property, it tells CSS to wrap items. This means extra items move into a new row or column. The break point of where the wrapping happens depends on the size of the items and the size of the container.

CSS also has options for the direction of the wrap:

- `nowrap`: this is the default setting, and does not wrap items.
- `wrap`: wraps items from left-to-right if they are in a row, or top-to-bottom if they are in a column.
- `wrap-reverse`: wraps items from bottom-to-top if they are in a row, or right-to-left if they are in a column.

```html
<style>
    #box-container {
        background: gray;
        display: flex;
        height: 100%;
        flex-wrap: wrap;
    }
    #box-1 {
        background-color: dodgerblue;
        width: 25%;
        height: 50%;
    }

    #box-2 {
        background-color: orangered;
        width: 25%;
        height: 50%;
    }
    #box-3 {
        background-color: violet;
        width: 25%;
        height: 50%;
    }
    #box-4 {
        background-color: yellow;
        width: 25%;
        height: 50%;
    }
    #box-5 {
        background-color: green;
        width: 25%;
        height: 50%;
    }
    #box-6 {
        background-color: black;
        width: 25%;
        height: 50%;
    }
</style>

<div id="box-container">
    <div id="box-1"></div>
    <div id="box-2"></div>
    <div id="box-3"></div>
    <div id="box-4"></div>
    <div id="box-5"></div>
    <div id="box-6"></div>
</div>
```

<br>

### Use the flex-shrink Property to Shrink Items

So far, all the properties in the challenges apply to the flex container (the parent of the flex items). However, there are several useful properties for the flex items.

The first is the `flex-shrink`property. When it's used, it allows an item to shrink if the flex container is too small. Items shrink when the width of the parent container is smaller than the combined widths of all the flex items within it.

The `flex-shrink`property takes numbers as values. The higher the number, the more it will shrink compared to the other items in the container. For example, if one item has a `flex-shrink`value of 1 and the other has a `flex-shrink`value of 3, the one with the value of 3 will shrink three times as much as the other.

```html
<style>
    #box-container {
        display: flex;
        height: 500px;
    }
    #box-1 {
        background-color: dodgerblue;
        width: 100%;
        height: 200px;
        flex-shrink: 1;
    }

    #box-2 {
        background-color: orangered;
        width: 100%;
        height: 200px;
        flex-shrink: 2;
    }
</style>

<div id="box-container">
    <div id="box-1"></div>
    <div id="box-2"></div>
</div>
```

<br>

### Use the flex-grow Property to Expand Items

The opposite of `flex-shrink`is the `flex-grow`property. Recall that `flex-shrink`controls the size of the items when the container shrinks. The `flex-grow`property controls the size of items when the parent container expands.

Using a similar example from the last challenge, if one item has a `flex-grow`value of 1 and the other has a `flex-grow`value of 3, the one with the value of 3 will grow three times as much as the other.

```html
<style>
    #box-container {
        display: flex;
        height: 500px;
    }

    #box-1 {
        background-color: dodgerblue;
        height: 200px;
        flex-grow: 1;
    }

    #box-2 {
        background-color: orangered;
        height: 200px;
        flex-grow: 2;
    }
</style>

<div id="box-container">
    <div id="box-1"></div>
    <div id="box-2"></div>
</div>
```

<br>

### Use the flex-basis Property to Set the Initial Size of an Item

The `flex-basis`property specifies the initial size of the item before CSS makes adjustments with `flex-shrink`or `flex-grow`.

The units used by the `flex-basis`property are the same as other size properties (`px`, `em`, `%`, etc.). The value `auto`sizes items based on the content.

```html
<style>
    #box-container {
        display: flex;
        height: 500px;
    }

    #box-1 {
        background-color: dodgerblue;
        height: 200px;
        flex-basis: 10em;
    }

    #box-2 {
        background-color: orangered;
        height: 200px;
        flex-basis: 20em;
    }
</style>

<div id="box-container">
    <div id="box-1"></div>
    <div id="box-2"></div>
</div>
```

<br>

### Use the flex Shorthand Property

There is a shortcut available to set several flex properties at once. The `flex-grow`, `flex-shrink`, and `flex-basis`properties can all be set together by using the `flex`property.

For example, `flex: 1 0 10px;`will set the item to `flex-grow: 1;`, `flex-shrink: 0;`, and `flex-basis: 10px;`.

The default property settings are `flex: 0 1 auto;`.

```html
<style>
    #box-container {
        display: flex;
        height: 500px;
    }
    #box-1 {
        background-color: dodgerblue;
        flex: 2 2 150px;
        height: 200px;
    }

    #box-2 {
        background-color: orangered;
        flex: 1 1 150px;
        height: 200px;
    }
</style>

<div id="box-container">
    <div id="box-1"></div>
    <div id="box-2"></div>
</div>
```

<br>

### Use the order Property to Rearrange Items

The `order`property is used to tell CSS the order of how flex items appear in the flex container. By default, items will appear in the same order they come in the source HTML. The property takes numbers as values, and negative numbers can be used.

```html
<style>
    #box-container {
        display: flex;
        height: 500px;
    }
    #box-1 {
        background-color: dodgerblue;
        order: 2;
        height: 200px;
        width: 200px;
    }

    #box-2 {
        background-color: orangered;
        order: 1;
        height: 200px;
        width: 200px;
    }
</style>

<div id="box-container">
    <div id="box-1"></div>
    <div id="box-2"></div>
</div>
```

<br>

### Use the align-self Property

The final property for flex items is `align-self`. This property allows you to adjust each item's alignment individually, instead of setting them all at once. This is useful since other common adjustment techniques using the CSS properties `float`, `clear`, and `vertical-align`do not work on flex items.

`align-self`accepts the same values as `align-items`and will override any value set by the `align-items`property.

```html
<style>
    #box-container {
        display: flex;
        height: 500px;
    }
    #box-1 {
        background-color: dodgerblue;
        align-self: center;
        height: 200px;
        width: 200px;
    }

    #box-2 {
        background-color: orangered;
        align-self: flex-end;
        height: 200px;
        width: 200px;
    }
</style>

<div id="box-container">
    <div id="box-1"></div>
    <div id="box-2"></div>
</div>
```

