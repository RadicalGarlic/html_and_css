# Lists
## Ordered Lists
Ordered (numbered) lists are marked with `<ol>` tags with the individual list items marked with `<li>`. Sometimes a `type` attribute is used with the `<ol>` tag to control if the list is numbered with numbers, letters, roman numerals, or whatever else. It's better to do that with CSS though.
```html
<html>
    <body>
        <ol>
            <li>Item one</li>
            <li>Item two</li>
        </ol>
    </body>
</html>
```

## Unordered Lists
Unordered lists are marked with `<ul>`. The list items are still marked with `<li>`. The `<ul>` tag can also have a `type` attribute to control the style of bullet points, but it's better to do that with CSS instead.
```html
<html>
    <body>
        <ul>
            <li>Item</li>
            <li>Another item</li>
        </ul>
    </body>
</html>
```

## Definition Lists
A defintion list consists of a series of terms and their definitions.
Definition lists are marked with `<dl>`. The list items are marked with `<dt>` for the terms and `<dd>` for the definitions.
```html
<html>
    <body>
        <dl>
            <dt>Urza</dt>
            <dd>Some dude</dd>

            <dt>Mishra</dt>
            <dd>Some other dude</dd>

            <dt>Blue</dt>
            <dt>Red</dt>
            <dd>Colors I think</dd>
        </dl>
    </body>
</html>
```

## Nesting Lists
All lists can be nested by specifying a list in `<li>`.
```html
<html>
    <body>
        <ol>
            <li>Number one</li>
            <li>
                <dl>
                    <dt>Some term</dt>
                    <dd>Some definition</dd>
                </dl>
            </li>
        </ol>
    </body>
</html>
```
