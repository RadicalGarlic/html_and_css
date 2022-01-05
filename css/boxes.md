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
