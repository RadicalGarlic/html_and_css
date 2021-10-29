# Extras
## id Attribute
Every HTML element can have the `id` attribute. The value for the attribute must be unique throughout the HTML document and must start with either a letter or underscore. The attribute is useful for allowing CSS/JS to operate on elements.

## class Attribute
Every HTML element can have the `class` attribute. The `class` attribute specifies the "type" of an element, and is useful for applying CSS/JS logic to elements marked as a certain class.

## Block Elements
Block elements are elements that always render on a new line. Examples include `h1`, `p`, `ul`, and `li`.

## Inline Elements
Inline elements are elements that will continue on the same line as any neighboring elements. Examples include `a`, `b`, `em`, and `img`.

## Grouping Elements with div
The `div` element can be used to group multiple elements into a single block element. This is useful for applying CSS to a group of elements.
```html
<!DOCTYPE html>
<html>
    <body>
        <div id="header">
            <h1>HEADER</h1>
            <p>It's ya boi</p>
        </div>
    </body>
</html>
```

## Grouping Elements with span
The `span` element can be used to group elements into a single inline element. This is useful for applying CSS to a group elements, except inline this time!
```html
<!DOCTYPE html>
<html>
    <body>
        <p>Lorem ipsum <span class="big"><b>BOI</b></span></p>
    </body>
</html>
```

## iframes
The `iframe` element creates a little window that can be used to embed an HTML document from another website into your own. This allows for embedding little widgets from other websites into your own.

The term "iframe" is short for "inline frame".

```html
<!DOCTYPE html>
<html>
    <body>
        <!-- width and height are in pixels -->
        <iframe width="450" height="350" src="https://localhost">
        </iframe>
    </body>
</html>
```

The `scrolling` attribute is an older attribute that will not be supported in HTML5. It can be set to the value "yes" or "no" and controls whether or not the iframe will have scrollbars. Scrollbars appear on iframes if the width/height are too small to show full iframe content.

The `frameborder` attribute is an older attribute that will not be supported in HTML5. It can be set to one of "0" or "1" and controls whether or not a border will be rendered around the iframe.

The `seamless` attribute is a new HTML5 attribute. If present, scrollbars will not appear on the iframe. This attribute does not require a value, but a value can still be set.
```html
<!DOCTYPE html>
<html>
    <body>
        <!-- width and height are in pixels -->
        <iframe width="450" height="350" src="https://localhost" seamless>
        </iframe>
    </body>
</html>
```

## Page Metainformation
Within the `head` element, `meta` elements can be used to specify key/value pairs that contain information about the page itself (page description, its author, etc.).

The following are commonly used `meta` values.
```html
<html>
    <head>
        <!--
            Commonly read by search engines.
            Should only contain a maximum of 155 characters.
            Sometimes displayed in search engine results.
        -->
        <meta name="description" content="my page" />

        <!--
            Comma-separated list of keywords that search engines used to care
            about. No longer really does anything.
        -->
        <meta name="keywords" content="stuff,crap" />

        <!--
            Indicates if the author wishes for this page to be used by search
            engines. Hopefully it is respected. A value of "noindex" indicates
            to not include this page in search results. A value of "nofollow"
            indicates that the page can be added to search results, but not any
            pages it links to.
        -->
        <meta name="robots" content="noindex" />

        <!--
            The "http-equiv" attribute is used in lieu of "name" for some
            values.
        -->
        <meta http-equiv="author" content="me" />
        
        <!-- Prevents browser caching of the page. -->
        <meta http-equiv="pragma" content="no-cache" />

        <!--
            Specifies when the cached page should expire, if cached by the
            browser. The timestamp format is very specific.
        -->
        <meta http-equiv="expires" content="Fri, 04 Apr 2014 23:59:59 GMT" />
    </head>
</html>
```

## Escape Characters
To enter in reserved or special characters (like angle brackets or the copyright symbol) in an HTML page, you'll need to enter its escape code. Escape characters have two formats.

|Character|Escape codes|
|-|-|
|<|`&lt;` `&#60;`|
|&|`&amp;` `&#38;`|
