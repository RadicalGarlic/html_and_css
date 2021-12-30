# Introduction
HTML stands for "HyperText Markup Language". The "HyperText" part refers to the fact that HTML pages can have links to other pages that allow for users to traverse pages quickly and easily. The "markup" part refers to how tags are used to mark up text.

## History
HTML4 was released in 1997, and is still mostly similar to HTML today (2021).

XHTML 1.0 was released in 2000. When XML was released in 1998, it was decided that HTML4 should be reformulated to adhere to the more strict rules of XML. For example...
1. Every element needs a closing tag (except for empty elements like `<img />`).
1. Attribute names must be lower case.
1. All attributes need a value, which must be enclosed in double quotes.
1. Deprecated elements were removed.
1. Every inner element opened inside an outer element must be closed inside the outer element.

This allowed for XML parsers to also work for XHTML.

HTML5 was released in 2008 and is still the most recent version of HTML as of 2021, although there have been modifications since. If an older browser that doesn't support HTML5 encounters a page with HTML5 elements, it simply doesn't display the HTML5 elements.

## General Structure
The contents of an HTML file describe an HTML document. The document is plain text that is marked up with various tags. Web browsers read these files and then display the web page depending on how things are marked up.

Here's an example.
```html
<!DOCTYPE html>
<html>
    <!-- This is a comment. -->
    <head>
        <title>Displays above the URL bar</title>
    </head>
    <body>
        Displayable text
    </body>
</html
```

Every HTML file should have a DOCTYPE that specifies which version of HTML the document adheres to. A list of available DOCTYPEs can be found [here](doctype.md).

The things enclosed in tags are called "elements".

HTML documents begin and end in `<html>` tags.

The `<head>` element contains info about the page. The contents of `<head>` don't actually show up on the web page. It usually has a `<title>` tag inside of it. The content of the `<title>` element appears in the space above the web browser's URL bar.

The `<body>` element marks what should appear in the main browser window, and typically makes up the bulk of the HTML document.

Markup tags can be classified as either "structural" markup or "semantic" markup. Structural markup affects the structure of web page (`body`, quote, headings, paragraph, etc.). Semantic markup adds meaning to the text it encloses (bold, italic, emphasis, etc.).

## Attributes
An HTML element can also have "attributes".
```html
<!-- The attribute name is "lang" and the attribute value is "en-us". -->
<p lang="en-us">English text</p>
```

If an attribute can accept multiple values, the values are specified in a space-separated list.
```html
<p class="class1 class2"></p>
```
