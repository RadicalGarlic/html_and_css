# Boxes
Remember that CSS treats each HTML element as if it was in its own box. CSS can be used to manipulate the appearance of this box (dimensions, borders, margins, show/hide, etc.).

## Box Dimensions
The default size of a box is just big enough to contain its element. This size can be modified in units of pixels/percentage/ems. Using percentages/ems as the units is useful for making sure things still look good in different screen sizes.

When specified in percentages, the box size is relative to the size of browser window unless the box is contained within another box. Then, the size is relative to the containing box's size.

When specified in ems, the box size is relative to the text within it.

```html
<!DOCTYPE html>
<html>
    <head>
        <style type="text/css">
            div {
                height: 300px;
                width: 400px;
                background-color: #ee3e80;
            }
            p {
                /* Size is 75% of containing div. */
                height: 75%;
                width: 75%;
                background-color: #e1ddda;
            }
        </style>
    </head>
    <body>
        <div>
            <p>
                asdfasdfasdfasdfasdf
            </p>
        </div>
    </body>
</html>
```

### Box Dimension Limits
Because some page designs expand and shrink with different window size, it's useful to specify minimums and maxiumus for height and width so things are always legible.
```css
div.someClass {
    min-width: 480px;
    max-width: 650px;
    min-height: 10px;
    max-height: 30px;
}
```

If the box is not big enough to hold the content, the content will overflow the bounds of the box which will looks pretty messy. The overflow behavior can be controlled with the `overflow` property (discussed next).

### Overflowing Content
The `overflow` property controls the appearance of elements that overflow beyond the bounds of their CSS box.
```css
p.hidden {
    /* Any overflowing content does not appear. */
    overflow: hidden;
}
p.scroll {
    /* Scrollbar is added to the box if content overflows. */
    overflow: scroll;
}
```

## Borders, Margins, and Padding
Every box can have the appearance of its borders, margins, and padding customized.

The border is the line that shows the edge of the box.

The margin sits outside the border, therefore creating gaps between other boxes. If the bottom of a margin touches any top margin, the browser will only show the larger of the two. If the margins are equal, the browser will only show one.

The padding is the space between the border of a box and its contained content. Adding padding can help with readability.

It's generally bad for readability to have boxes touching each other or for the content/words within a box go right up to the border.

### Borders
#### Border Width
Border width is controlled with the `border-width` property. Percentages cannot be used with this property.
```css
p.classOne {
    border-width: medium;
}

p.classTwo {
    border-top-width: 1px;
    border-right-width: 2px;
    border-bottom-width: 3px;
    border-left-width: 4px;
}

/*
    Equivalent to...
        border-top-width: 1px;
        border-right-width: 2px;
        border-bottom-width: 3px;
        border-left-width: 4px;
*/
p.classThree {
    border-width: 1px 2px 3px 4px;
}
```

#### Border Style
The border style is controlled with the `border-style` property. This property can only be set to one of the following values.
1. `solid`
1. `dotted`
1. `dashed`
1. `double`
1. `groove`
1. `ridge`
1. `inset`
1. `outset`
1. `hidden` (equivalent to `none`)
1. `none` (equivalent to `hidden`)

```css
p.classOne {
    border-style: solid;
}

p.classTwo {
    border-top-style: solid;
    border-left-style: dotted;
    border-bottom-style: dashed;
    border-right-style: double;
}
```

#### Border Color
Border color is controlled with the `border-color` property. It can be set to RGB, hex codes, CSS color names, or CSS3 HSL values as described in [Color](color.md).

```css
p.classOne {
    border-color: #ffffff;
}

p.classTwo {
    border-top-color: #000000;
    border-right-color: #000001;
    border-bottom-color: #000002;
    border-left-color: #000003;
}

/*
    Equivalent to...
        border-top-color: #000000;
        border-right-color: #000001;
        border-bottom-color: #000002;
        border-left-color: #000003;
*/
p.classThree {
    border-color: #000000 #000001 #000002 #000003;
}
```

#### Shorthand
Border width, style, and color and be controlled in a single `border` property (although different values for top/right/bottom/left cannot be specified).
```css
p {
    /* 3px width, solid style, #000000 color */
    border: 3px solid #000000;
}
```

### Padding
The `padding` property controls the amount of space between the box's contained elements and the border. It's usually specified in pixels although percentages and ems are possible. Percentages are relative to the browser window or containing box if there is one.

If a box has width specified, the padding is added onto the width.

```css
p.someClass {
    padding: 10px;
}

p.someOtherClass {
    padding-top: 1px;
    padding-right: 2px;
    padding-bottom: 3px;
    padding-left: 4px;
}

/*
    Equivalent to setting top and bottom to 10px and left and right to 20px.
*/
p.shorthandClass 
    padding: 10px 20px;
}

/*
    Equivalent to...
        padding-top: 1px;
        padding-right: 2px;
        padding-bottom: 3px;
        padding-left: 4px;
*/
p.otherShorthandClass {
    padding: 1px 2px 3px 4px;
}
```

The `padding` property is NOT inherited by child elements.

### Margin
The `margin` property controls the amount of space between boxes. It's usually specified in pixels although percentages and ems are possible.

If boxes sit on top of each other, only the larger of the two (top vs. bottom) will be shown. If both are equal, only one will be shown.

```css
p.someClass {
    margin: 10px;
}

p.someOtherClass {
    margin-top: 1px;
    margin-right: 2px;
    margin-bottom: 3px;
    margin-left: 4px;
}

/*
    Equivalent to setting top and bottom to 10px and left and right to 20px.
*/
p.shorthandClass {
    margin: 10px 20px;
}

/*
    Equivalent to...
        margin-top: 1px;
        margin-right: 2px;
        margin-bottom: 3px;
        margin-left: 4px;
*/
p.otherShorthandClass {
    margin: 1px 2px 3px 4px;
}
```

The `margin` property is also NOT inherited by child elements.

## Centering Content
To center a box on a page or within another box, set the left and right margins to `auto`. Also make sure to set the width of the box to some value or else it will span the entire width of the page or containing box.
```css
p.someClass {
    width: 400px;
    margin: 10px auto;
}
```

In older browsers (particularly IE6), the element should also have `text-align` set to `center`. The property is also inherited by child elements, so it would need to be overridden if child text/elements should not be also centered.

## IE6 Boxes
Internet Explorer 6 infamously had unique rules about its boxes.

By default, IE6 includes the padding and margins to the width of the box instead of adding the padding and margin values to the width. This means that if padding + margin was greater than width, it the padding and width wouldn't show up. Adding the doctype for HTML5, HTML4 strict, or HTML4 transitional will force IE6 to use the standard behavior.

## Changing Between Inline and Block
The `display` property can change elements between inline and block elements.
```css
p.classOne {
    /* Force block elements to be inline. */
    display: inline;
}

p.classTwo {
    /* Force inline elements to be block. */
    display: block;
}

p.classThree {
    /*
        Force block elements to flow like inline elements, but still retain
        other features of block elements.
    */
    display: inline-block;
}

p.classFour {
    /* */
    display: none;
}
```
