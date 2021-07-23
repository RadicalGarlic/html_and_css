# Structure
HTML stands for "HyperText Markup Language". The "HyperText" part refers to the fact that HTML pages can have links to other pages that allow for users to traverse pages quickly and easily. The "markup" part refers to how tags are used to "mark up" text.

HTML5 is the latest major version of HTML at the time of writing (2021) and introduces many new changes. It was released in 2008. If an older browser that doesn't support HTML5 encounters a page with HTML5 elements, it simply doesn't display the HTML5 elements.

An HTML file describes a document. The document is plain text that is marked up with various tags. Web browsers read these files and then display the web page depending on how things are marked up.
```html
<html>
    <body>
        Plain text
    </body>
</html
```

The things enclosed in tags are called "elements".

HTML documents begin and end in `<html>` tags.

An HTML element can also have "attributes".
```html
<!-- This is a comment. -->
<!-- The attribute name is "lang" and the attribute value is "en-us". -->
<p lang="en-us">English text</p>
```

The `<head>` element contains info about the page. The contents of `<head>` don't actually show up on the web page. It usually has a `<title>` tag inside of it. The content of the `<title>` element appears in the space above the web browser's URL bar.

The `<body>` element marks what should appear in the main browser window.

```html
<html>
    <head>
        <title>Displays above the URL bar</title>
    </head>
    <body>Displayable text</body>
</html>
```

