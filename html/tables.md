# Tables
Tables in HTML are as one would expect: a grid of cells (rows and columns). Not all browsers draw lines around the cells. This can be controlled with CSS.
```html
<html>
    <body>
        <table>
            <tr> <!-- table row -->
                <td>first row, first col</td> <!-- table data (a cell) -->
                <td>first row, second col</td>
            </tr>
            <tr>
                <td></td> <!-- Always represent empty cells so things will
                               render correctly. -->
                <td>second row, second col</td>
            </tr>
        </table>
    </body>
</html>
```

## Row/Column Headings
Tables can be given headings with the `th` element.
```html
<html>
    <body>
        <table>
            <tr>
                <th></th> <!-- Empty table heading so things will render
                               properly. This is the top-left cell. -->
                <th scope="col">Column 1</th>
                <th scope="col">Column 2</th>
            </tr>
            <tr>
                <th scope="row">Row 1</th>
                <td>(r1,c1)</td>
                <td>(r1,c2)</td>
            </tr>
            <tr>
                <th scope="row">Row 2</th>
                <td>(r2,c1)</td>
                <td>(r2,c2)</td>
            </tr>
        </table>
    </body>
</html>
```

## Spanning Rows/Columns
Sometimes it's useful to have a table entry/heading span multiple rows/columns. This can be done with the `colspan` and `rowspan` attributes.
```html
<html>
    <body>
        <table>
            <tr>
                <th></th>
                <th scope="col">Col 1</th>
                <th scope="col">Col 2</th>
            </tr>
            <tr>
                <th scope="row">Row 1</th>
                <td>(r1,c1)</td>
                <td>(r1,c2)</td>
            </tr>
            <tr>
                <th scope="row">Row 2</th>
                <td colspan="2">(r2,c1+2)</td>
            </tr>
            <tr>
                <th scope="row" rowspan="2">Row 3+4</th>
                <td>(r3,c1)</td>
                <td>(r3,c2)</td>
            </tr>
            <tr>
                <td>(r4,c1)</td>
                <td>(r4,c2)</td>
            </tr>
        </table>
    </body>
</html>
```

## Long Tables
For longer tables, it may be useful to mark some rows and the table header and footer using the `thead`, `tbody`, and `tfoot` elements.
```html
<html>
    <body>
        <table>
            <thead>
                <tr>
                    <th></th>
                    <th scope="col">Col 1</th>
                    <th scope="col">Col 2</th>
                    <th scope="col">Col 3</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <th scope="row">Row 1</th>
                    <td>(r1,c1)</td>
                    <td>(r1,c2)</td>
                    <td>(r1,c3)</td>
                </tr>
            </tbody>
            <tfoot>
                <tr>
                    <th scope="row">Row 2 (foot)</th>
                    <td>(r2,c1)</td>
                    <td>(r2,c2)</td>
                    <td>(r2,c3)</td>
                </tr>
            </tfoot>
        </table>
    </body>
</html>
```

On some browsers, if the table is long enough that it scrolls off the screen and the user scrolls down/up, the header and footer rows of the table are always visible. This is very useful for making column headings always visible. This is not the default behavior for many browsers though.

The header and footer elements also make modifying the top/bottom rows with CSS more convenient.

## Pre-HTML5 Code
The following elements/attributes are considered to be oudated, but they may be encountered when working with older codebases. All these elements/attributes have been replaced by the use of CSS.

### Width & Spacing
The `width` attribute could be used on `td`, `th`, or `table` elements to specify the width of columns in pixels. When used in the `table` element, this controlled the column width for the whole table. When used in the `td` or `th` elements, it only modified the width of that specific cell.

The `table` tag can also use the `cellpadding` and `cellspacing` attributes. `cellpadding` controls the space inside each cell, and `cellspacing` controls the space between cells. Both attributes work in units of pixels.

```html
<html>
    <body>
        <table width="400" cellpadding="10" cellspacing="5">
            <tr>
                <td>(r1,c1)</td>
                <td>(r1,c2)</td>
            </tr>
        </table>
    </body>
</html>
```

### Border & Background
The `border` attribute can be used on both `table` and `td` elements to set a border between cells. The attribute value is the border width in pixels.

The `bgcolor` attribute is used to indicate background color of either the whole table or specific cells.

```html
<html>
    <body>
        <table border="2" bgcolor="#efefef">
            <tr>
                <td bgcolor="#cccccc">(r1,c1)</td>
            </tr>
        </table>
    </body>
</html>
```
