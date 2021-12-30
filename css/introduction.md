# Introduction
CSS stands for Cascading Style Sheets.

CSS influences the appearance of the web page (typeface, color, size, position, etc.).

To understand how CSS works, pretend there's an invisible box drawn around every HTML element. CSS influences how that box and everything contained in it appears. Specifically, CSS adds styling rules that are associated with one or more HTML elements.

## Syntax
A CSS rule consists of a selector and a declaration.
```css
/* This is a single-line comment */
/*
    This is a multi-line comment. Same syntax as a single-line comment, which is
    a bit weird honestly.
*/
/* This rule specifies that all <p> elements should have the typeface Arial. */
p {
    font-family: Arial;
}
```
In the above example, the selector is `p` and the declaration is `font-family: Arial;`.

Declarations are property-value pairs. In the declaration `font-family: Arial;`, `font-family` is the property and `Arial` is the value.

CSS rules can have multiple selectors and declarations.
```css
/*
    All h1, h2, and h3 elements should have the Arial typeface and color yellow.
*/
h1, h2, h3 {
    font-family: Arial;
    color: yellow;
}
```

## Usage with HTML
### Internal
CSS rules can be inserted directly into HTML between `style` tags.
```html
<!DOCTYPE html>
<html>
    <head>
        <style type="text/css">
            body {
                background-color: rgb(158,179,175);
            }
            h1 {
                color: red;
            }
        </style>
    </head>
    <body>
        <h1>RED HEADING</h1>
    </body>
</html>
```

Most elements used to have a `style` attribute that could take CSS in the days of HTML4 and Transitional XHTML. It should be avoided today.
```html
<html>
    <body>
        <p style="color:red">red text</p>
    </body>
</html>
```

On any website with multiple web pages, CSS should be written an external file and linked to from HTML pages rather than be written directly into the HTML pages themselves.

### External
The `link` HTML element is used to link HTML pages to external CSS files.
```html
<!DOCTYPE html>
<html>
    <head>
        <link href="path/to/css/styles.css" type="text/css" rel="stylesheet" />
    </head>
    <body>
        <p>text</p>
    </body>
</html>
```
The `href` attribute specifies the file location of the CSS file.

The `type` attribute specifies the type of data in CSS file. It should always be `text/css`.

The `rel` attribute specifies the the relationship between the linked file and the HTML page. For CSS files, it should always be `stylesheet`.

Multiple `link` elements can be used to link to multiple CSS files for a single web page. Some people like to have a separate CSS files for presentation and layout.

## Selectors
CSS selectors can select by many things (element type, class, attributes and their values, etc.).

Below is a list containing the most common ones.
<table>
    <tr>
        <td><code class="langauage-css">* {}</code></td>
        <td>Universal. Applies to all elements in the document.</td>
    </tr>
    <tr>
        <td><code class="language-css">someHtmlElement {}</code></td>
        <td>Matches all HTML elements of the given type. For example, <code>p {}</code> would match all <code>&lt;p&gt;</code> elements.</td>
    </tr>
    <tr>
        <td><code class="language-css">.classAttrValue {}</code></td>
        <td>Matches all elements with <code>class</code> attribute "classAttrValue".</td>
    </tr>
    <tr>
        <td><code class="language-css">p.classAttrValue {}</code></td>
        <td>Matches all <code>&lt;p&gt;</code> elements with class value "classAttrValue".</td>
    </tr>
    <tr>
        <td><code class="language-css">#idAttrValue {}</code></td>
        <td>Matches all elements with <code>id</code> attribute value "idAttrValue"</td>
    </tr>
    <tr>
        <td><code class="language-css">someHtmlElement>someOtherHtmlElement {}</code></td>
        <td>Matches all elements of type "someOtherHtmlElement" that are direct children of "someHtmlElement". For example, <code>li&gt;a {}</code> matches all <code>&lt;a&gt;</code> elements that are direct children of a <code>&lt;li&gt;</code> element.
    </tr>
    <tr>
        <td><code class="language-css">someElement someOtherElement {}</code></td>
        <td>Matches all "someOtherElement" type elements that are descendants within a "someElement", no matter how deep.</td>
    </tr>
    <tr>
        <td><code class="language-css">someElement+someOtherElement {}</code></td>
        <td>Matches the first "someOtherElement" element after any "someElement" has been closed (siblings).</td>
    </tr>
    <tr>
        <td><code class="language-css">someElement~someOtherElement {}</code></td>
        <td>Matches all "someOtherElement" elements that are siblings of a "someElement" element.</td>
    </tr>
    <tr>
        <td><code class="language-css">someElement[someAttr]</code> (existence)</td>
        <td>Matches any element with the specified attribute, no matter the attribute's value.</td>
    </tr>
    <tr>
        <td><code class="language-css">someElement[someAttr="val"]</code> (equality)</td>
        <td>Matches any element with the specified attribute set to the specified value.</td>
    </tr>
    <tr>
        <td><code class="language-css">someElement[someAttr~="val"]</code> (space)</td>
        <td>Matches any element with the specified attribute that contains the specified value in its space-separated list of values.</td>
    </tr>
    <tr>
        <td><code class="language-css">someElement[someAttr^"prefix"]</code> (prefix)</td>
        <td>Matches any element with the specified attribute whose value starts with the specified prefix.</td>
    </tr>
    <tr>
        <td><code class="language-css">someElement[someAttr*"substring"]</code> (substring)</td>
        <td>Matches any element with the specified attribute whose value contains the specified substring.</td>
    </tr>
    <tr>
        <td><code class="language-css">someElement[someAttr$"suffix"]</code> (suffix)</td>
        <td>Matches any element with the specified attribute whose value ends ith the specified suffix.</td>
    </tr>
</table>

## How Rules Cascade
If two or more rules apply to the same element, if the two selectors are identical, then the last rule will take place.

Else, if one selector is more specific than the other, then the more specific rule will take place.

Else, if one property is marked with `!important`, then it will override any non-important property and the containing rule will override other non-important rules.
```css
h1 {
    color: blue !important;
}
```

With these rules, you can specify general rules and then override them with more specific ones as needed.

## Inheritance
Specifying `font-family` or `color` on the `<body>` element will apply to most child elements because they are "inherited" properties.

Properties like `background-color` or `border` are not inherited properties.

Inheritance can be forced by specifying `inherit` for the property value.
```css
.page {
    border: 1px solid #665544;
    padding: inherit;
}
```

## Browser Quirks
The first version of CSS was released in 1996, and CSS2 was released two years later in 1998.

CSS3 is the current standard at the time of writing (2021).

Because each web browser and version can display each CSS property slightly differently, make sure to test a web page on all major browsers and multiple older versions.

Sites like `browsercam.com`, `browserlab.adobe.com`, `browsershots.org`, and `crossbrowsertesting.com` can help avoid having to download and install multiple browsers.

There some sites dedicated to documenting these browser quirks/differences.
* `positioniseverything.net`
* `quirksmode.org`
