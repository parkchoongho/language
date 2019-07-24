# Introduction to the CSS Grid Challenges

CSS Grid helps you easily build complex web designs. It works by turning an HTML element into a grid container with rows and columns for you to place children elements where you want within the grid.

<br>

<br>

### Create Your First CSS Grid

Turn any HTML element into a grid container by setting its `display`property to `grid`. This gives you the ability to use all the other properties associated with CSS Grid.

**Tip**: In CSS Grid, the parent element is referred to as the container and its children are called items.

```html
<style>
    .d1{background:LightSkyBlue;}
    .d2{background:LightSalmon;}
    .d3{background:PaleTurquoise;}
    .d4{background:LightPink;}
    .d5{background:PaleGreen;}

    .container {
        font-size: 40px;
        width: 100%;
        background: LightGray;
        /* add your code below this line */
        display: grid;

        /* add your code above this line */
    }
</style>

<div class="container">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
```

<br>

### Add Columns with grid-template-columns

Simply creating a grid element doesn't get you very far. You need to define the structure of the grid as well. To add some columns to the grid, use the `grid-template-columns`property on a grid container as demonstrated below:

```css
.container {
    display: grid;
    grid-template-columns: 50px 50px;
}
```

This will give your grid two columns that are 50px wide each.

The number of parameters given to the `grid-template-columns`property indicates the number of columns in the grid, and the value of each parameter indicates the width of each column.

```html
<style>
    .d1{background:LightSkyBlue;}
    .d2{background:LightSalmon;}
    .d3{background:PaleTurquoise;}
    .d4{background:LightPink;}
    .d5{background:PaleGreen;}

    .container {
        font-size: 40px;
        width: 100%;
        background: LightGray;
        display: grid;
        /* add your code below this line */
        grid-template-columns: 100px 100px 100px;

        /* add your code above this line */
    }
</style>

<div class="container">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
```

<br>

### Add Rows with grid-template-rows

The grid you created in the last challenge will set the number of rows automatically. To adjust the rows manually, use the `grid-template-rows`property in the same way you used `grid-template-columns`in previous challenge.

```html
<style>
    .d1{background:LightSkyBlue;}
    .d2{background:LightSalmon;}
    .d3{background:PaleTurquoise;}
    .d4{background:LightPink;}
    .d5{background:PaleGreen;}

    .container {
        font-size: 40px;
        width: 100%;
        background: LightGray;
        display: grid;
        grid-template-columns: 100px 100px 100px;
        /* add your code below this line */
        grid-template-rows: 50px 50px;

        /* add your code above this line */
    }
</style>

<div class="container">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
```

<br>

### Use CSS Grid units to Change the Size of Columns and Rows

You can use absolute and relative units like `px`and `em`in CSS Grid to define the size of rows and columns. You can use these as well:

`fr`: sets the column or row to a fraction of the available space,

`auto`: sets the column or row to the width or height of its content automatically,

`%`: adjusts the column or row to the percent width of its container.

Here's the code that generates the output in the preview:

```css
grid-template-columns: auto 50px 10% 2fr 1fr;
```

This snippet creates five columns. The first column is as wide as its content, the second column is 50px, the third column is 10% of its container, and for the last two columns; the remaining space is divided into three sections, two are allocated for the fourth column, and one for the fifth.

```html
<style>
    .d1{background:LightSkyBlue;}
    .d2{background:LightSalmon;}
    .d3{background:PaleTurquoise;}
    .d4{background:LightPink;}
    .d5{background:PaleGreen;}

    .container {
        font-size: 40px;
        width: 100%;
        background: LightGray;
        display: grid;
        /* modify the code below this line */

        grid-template-columns: 1fr 100px 2fr;

        /* modify the code above this line */
        grid-template-rows: 50px 50px;
    }
</style>

<div class="container">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
```

<br>

### Create a Column Gap Using grid-column-gap

So far in the grids you have created, the columns have all been tight up against each other. Sometimes you want a gap in between the columns. To add a gap between the columns, use the `grid-column-gap`property like this:

```css
grid-column-gap: 10px;
```

This creates 10px of empty space between all of our columns.

```html
<style>
    .d1{background:LightSkyBlue;}
    .d2{background:LightSalmon;}
    .d3{background:PaleTurquoise;}
    .d4{background:LightPink;}
    .d5{background:PaleGreen;}

    .container {
        font-size: 40px;
        min-height: 300px;
        width: 100%;
        background: LightGray;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr 1fr;
        /* add your code below this line */
        grid-column-gap: 20px;

        /* add your code above this line */
    }
</style>

<div class="container">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
```

<br>

### Create a Row Gap using grid-row-gap

You can add a gap in between the rows of a grid using `grid-row-gap`in the same way that you added a gap in between columns in the previous challenge.

```html
<style>
    .d1{background:LightSkyBlue;}
    .d2{background:LightSalmon;}
    .d3{background:PaleTurquoise;}
    .d4{background:LightPink;}
    .d5{background:PaleGreen;}

    .container {
        font-size: 40px;
        min-height: 300px;
        width: 100%;
        background: LightGray;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr 1fr;
        /* add your code below this line */
        grid-row-gap: 5px;

        /* add your code above this line */
    }
</style>

<div class="container">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
```

<br>

### Add Gaps Faster with grid-gap

`grid-gap`is a shorthand property for `grid-row-gap`and `grid-column-gap`from the previous two challenges that's more convenient to use. If `grid-gap`has one value, it will create a gap between all rows and columns. However, if there are two values, it will use the first one to set the gap between the rows and the second value for the columns.

```html
<style>
    .d1{background:LightSkyBlue;}
    .d2{background:LightSalmon;}
    .d3{background:PaleTurquoise;}
    .d4{background:LightPink;}
    .d5{background:PaleGreen;}

    .container {
        font-size: 40px;
        min-height: 300px;
        width: 100%;
        background: LightGray;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr 1fr;
        /* add your code below this line */
        grid-gap: 10px 20px;

        /* add your code above this line */
    }
</style>
<div class="container">
    <div class="d1">1</div>
    <div class="d2">2</div>
    <div class="d3">3</div>
    <div class="d4">4</div>
    <div class="d5">5</div>
</div>
```

<br>

### Use grid-column to Control Spacing

Up to this point, all the properties that have been discussed are for grid containers. The `grid-column`property is the first one for use on the grid items themselves.

The hypothetical horizontal and vertical lines that create the grid are referred to as lines. These lines are numbered starting with 1 at the top left corner of the grid and move right for columns and down for rows, counting upward.

To control the amount of columns an item will consume, you can use the `grid-column`property in conjunction with the line numbers you want the item to start and stop at.

Here's an example:

> grid-column: 1 / 3;

This will make the item start at the first vertical line of the grid on the left and span to the 3rd line of the grid, consuming two columns.

```html
<style>
    .item1{background:LightSkyBlue;}
    .item2{background:LightSalmon;}
    .item3{background:PaleTurquoise;}
    .item4{background:LightPink;}

    .item5 {
        background: PaleGreen;
        /* add your code below this line */
        grid-column: 2 / 4;

        /* add your code above this line */
    }

    .container {
        font-size: 40px;
        min-height: 300px;
        width: 100%;
        background: LightGray;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr 1fr;
        grid-gap: 10px;
    }
</style>

<div class="container">
    <div class="item1">1</div>
    <div class="item2">2</div>
    <div class="item3">3</div>
    <div class="item4">4</div>
    <div class="item5">5</div>
</div>
```

<br>

### Use grid-row to Control Spacing

Of course, you can make items consume multiple rows just like you can with columns. You define the horizontal lines you want an item to start and stop at using the `grid-row`property on a grid item.

```html
<style>
    .item1{background:LightSkyBlue;}
    .item2{background:LightSalmon;}
    .item3{background:PaleTurquoise;}
    .item4{background:LightPink;}

    .item5 {
        background: PaleGreen;
        grid-column: 2 / 4;
        /* add your code below this line */
        grid-row: 2 / 4;

        /* add your code above this line */
    }

    .container {
        font-size: 40px;
        min-height: 300px;
        width: 100%;
        background: LightGray;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr 1fr;
        grid-gap: 10px;
    }
</style>

<div class="container">
    <div class="item1">1</div>
    <div class="item2">2</div>
    <div class="item3">3</div>
    <div class="item4">4</div>
    <div class="item5">5</div>
</div>
```

<br>

### Align an Item Horizontally using justify-self

In CSS Grid, the content of each item is located in a box which is referred to as a cell. You can align the content's position within its cell horizontally using the `justify-self`property on a grid item. By default, this property has a value of `stretch`, which will make the content fill the whole width of the cell. This CSS Grid property accepts other values as well:

`start`: aligns the content at the left of the cell,

`center`: aligns the content in the center of the cell,

`end`: aligns the content at the right of the cell.

```html
<style>
    .item1{background: LightSkyBlue;}

    .item2 {
        background: LightSalmon;
        /* add your code below this line */
        justify-self: center;

        /* add your code above this line */
    }

    .item3{background:PaleTurquoise;}
    .item4{background:LightPink;}
    .item5{background:PaleGreen;}

    .container {
        font-size: 40px;
        min-height: 300px;
        width: 100%;
        background: LightGray;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr 1fr;
        grid-gap: 10px;
    }
</style>

<div class="container">
    <div class="item1">1</div>
    <div class="item2">2</div>
    <div class="item3">3</div>
    <div class="item4">4</div>
    <div class="item5">5</div>
</div>
```

<br>

### Align an Item Vertically using align-self

Just as you can align an item horizontally, there's a way to align an item vertically as well. To do this, you use the `align-self`property on an item. This property accepts all of the same values as `justify-self`from the last challenge.

```html
<style>
    .item1{background:LightSkyBlue;}
    .item2{background:LightSalmon;}

    .item3 {
        background: PaleTurquoise;
        /* add your code below this line */
        align-self: end;

        /* add your code above this line */
    }

    .item4{background:LightPink;}
    .item5{background:PaleGreen;}

    .container {
        font-size: 40px;
        min-height: 300px;
        width: 100%;
        background: LightGray;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr 1fr;
        grid-gap: 10px;
    }
</style>

<div class="container">
    <div class="item1">1</div>
    <div class="item2">2</div>
    <div class="item3">3</div>
    <div class="item4">4</div>
    <div class="item5">5</div>
</div>
```

<br>

### Align All Items Horizontally using justify-items

Sometimes you want all the items in your CSS Grid to share the same alignment. You can use the previously learned properties and align them individually, or you can align them all at once horizontally by using `justify-items`on your grid container. This property can accept all the same values you learned about in the previous two challenges, the difference being that it will move **all** the items in our grid to the desired alignment.

```html
<style>
    .item1{background:LightSkyBlue;}
    .item2{background:LightSalmon;}
    .item3{background:PaleTurquoise;}
    .item4{background:LightPink;}
    .item5{background:PaleGreen;}

    .container {
        font-size: 40px;
        min-height: 300px;
        width: 100%;
        background: LightGray;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr 1fr;
        grid-gap: 10px;
        /* add your code below this line */
        justify-items: center;

        /* add your code above this line */
    }
</style>

<div class="container">
    <div class="item1">1</div>
    <div class="item2">2</div>
    <div class="item3">3</div>
    <div class="item4">4</div>
    <div class="item5">5</div>
</div>
```

