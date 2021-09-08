# Text
Structural markup is markup that specifies the structure of the web page text.

Semantic markup is markup that gives extra information like what text has emphasis or is a quote. This extra information can help search engines and screen readers read the web page more accurately.

## Structural Markup
### Headings
HTML has 6 levels of headings. Heading 1 gets displayed the largest and heading 6 gets displayed the smallest.
```html
<html>
    <body>
        <h1>Heading 1</h1>
        <h2>Heading 2</h2>
        <h3>Heading 3</h3>
        <h4>Heading 4</h4>
        <h5>Heading 5</h5>
        <h6>Heading 6</h6>
    </body>
</html>
```

### Paragraph
Paragraphs are marked with `<p>` tags. Paragraphs are usually separated by a newline.

Whitespace in `<p>` tags gets collapsed, so whitespace doesn't get rendered exactly as it's written.
```html
<html>
    <body>
        <p>First paragraph</p>
        <p>Second paragraph which is on a new line</p>
        <p>
            This text is all on            one
            line.
        </p>
    </body>
</html>
```

### Bold face
Text can be bolded with `<b>` tags.
```html
<html>
    <body>
        <p><b>This text is bold.</b> This text is not.</p>
    </body>
</html>
```

### Italics
Text can be italicized with `<i>` tags.
```html
<html>
    <body>
        <p><i>This text is italicized.</i> This text is not.</p>
    </body>
</html>
```

### Superscript and Subscript
Text can be superscripted with `<sup>` tags. Text can be subscripted with `<sub>`.
```html
<html>
    <body>
        <p>The 4<sup>th</sup></p>
        <p>H<sub>2</sub>O</p>
    </body>
</html>
```

### Line Breaks
The tag `<br />` is used to make line breaks in paragraphs.

The line break tag cannot enclose any text is one of the "empty elements" in HTML. Empty elements can be written without the extra space or `/`, so the tags `<br />`, `<br/>`, and `<br>` are all equivalent. Although they can be omitted, it's "good practice" to include the space and `/`.
```html
<html>
    <body>
        <p>This sentence is on...<br />...two lines.</p>
        <p>The linebreak tag<br/>can be written in<br>a couple different ways.</p>
    </body>
</html>
```

### Horizontal Rule
The tag `<hr />` creates a line break and a horizontal separating line. The `<hr />` tag is another empty element.
```html
<html>
    <body>
        <p>Top<hr />Bottom</p>
    </body>
</html>
```

## Semantic Markup
### Strong
The `<strong>` tag marks text with strong importance. It usually gets rendered as bold text.
```html
<html>
    <body>
        <strong>Very important</strong>
    </body>
</html>
```
### Emphasis
The `<em>` tag marks text with emphasis. It usually gets rendered as italics.
```html
<html>
    <body>
        <em>Emphasis</em>
    </body>
</html>
```

### Quotes
The `<q>` tag marks smaller quotes that can sit inline with a paragraph. It usually gets rendered with quotation marks, but the Internet Explorer browser doesn't. For this reason, a lot of people don't like to use this tag.

```html
<html>
    <body>
        <p>...and then he said <q cite="https://some-url.com">THE BIG SUCC</q>.</p>
    </body>
</html>
```

The `<blockquote>` tag marks a big quotation (around a paragraph in size). Blockquotes usually get rendered as indented text. Don't use `<blockquote>` just to indent things though. If all you need is indentation, use CSS instead.
```html
<html>
    <body>
        <blockquote cite="https://some-url.com">
            <p>Never gonna give you up</p>
        </blockquote>
    </body>
</html>
```

The quote tags both support a `cite` attribute which should be set to some URL that is the source for the given quote.

### Abbrebiations and Acronyms
The `<abbr>` tag marks abbreviations and acronyms. The full term is specified using the `title` attribute, which usually can be viewed by hovering over the text.
```html
<html>
    <body>
        <p><abbr title=Doctor>Dr.</abbr> Bobanas</p>
    </body>
</html>
```

There used to be a separate `<acronym>` element for acronyms specifically. Now in HTML 5, just the `<abbr>` tag is used.

### Citations
The `<cite>` tag marks a reference to a book, film, or research paper. The text is usually rendered as italics.
```html
<html>
    <body>
        <p>My favorite book is <cite>The Very Hungry Caterpillar</cite>.</p>
    </body>
</html>
```

Prior to HTML 5, `<cite>` was used for people's names. This should no longer be done in HTML 5, but a lot of people keep doing it anyways.

### Definition
The `<dfn>` tag is used to mark new terms that are being introduced for the first time and are being defined in the sentence. It is sometimes rendered in italics, but not all major browsers do so.
```html
<html>
    <body>
        <p>A <dfn>big banana</dfn> is a banana that is REALLY BIG YOU GUYS.</p>
    </body>
</html>
```

### Author Details
The `<address>` tag is used to contain contact details for the page author. It can contain a physical address, but can contain things like phone numbers or email addresses. Browsers usually display the text in italics.
```html
<html>
    <body>
        <address>
            <p>somedude@email.com</p>
            <p>1 (234) 567-8901</p>
            <p>
                USA<br />
                1234 SomeStreet Dr.<br />
                SomeCity, CA 13456
            </p>
        </address>
    </body>
</html>
```

Author contact information can also be written using the "hCard" microformat (http://microformats.org/wiki/h-card).

### Changes to Content
The `<ins>` tag marks up text that has been inserted into the page. It is usually rendered as underlining.

The `<del>` tag marks up text that has been no longer relevant, but is still shown as the page. It is usually rendered with a strikethrough.

The `<s>` tag marks up text that should have a strikethough. Really similar to the `<del>` tag.

HTML prior to HTML 5 had the `<u>` tag for underlining, but that's being phased out.

```html
<html>
    <body>
        <p>Here is the <del>old info</del> <ins>new info</ins>!</p>
        <p><s>Strikethrough</s></p>
    </body>
</html>
```
