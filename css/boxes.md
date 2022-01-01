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
