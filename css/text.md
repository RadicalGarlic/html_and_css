# Text
## Fonts
In order to use a text font, the web browser must already have it installed or the site must download it to the browser.

Web browsers are supposed to have least one font from each of these categories installed.
* serif
* sans-serif
* monospace
* cursive
* fantasy

Specific fonts from each category can be specified in CSS, but it's not guaranteed that the browser will have them installed. Because of this, multiple fonts can be specified in order of preference. This list of fonts is called the "font stack".
```css
/* Below are commonly installed fonts. */
/* Font preference is from left to right. */
h1 {
    font-family: Impact, Haettenschweiler, fantasy;
}
h2 {
    font-family: "Comic Sans MS", "Monotype Corsiva", cursive;
}
p.code {
    font-family: Courier, "Courier New", monospace;
}
p.serious {
    font-family: Arial, Verdana, Helvetica, sans-serif;
}
p {
    font-family: Georgia, Times, "Times New Roman", serif;
}
```

### Font Size
Font size can be specified in pixels, points (roughly equivalent to pixels), percentages, or EMs (width of the letter "m").
```css
body {
    font-family: serif;
    font-size: 12px;
}
h1 {
    font-size: 200%;
}
h2 {
    font-size: 1.3em;
}
```

The default text size on browsers is 16 pixels. Sizes written in percentages or EMs can be converted to pixels using this default size as a base. The default font size can be changed by the user (by zooming in/out on the page), and this change will be taken into account by font sizes written in percentages or EMs.

EMs specifically uses the text size of the parent element as a base.

A point refers to 1/72 of an inch, which is rougly equivalent to a pixel since most displays have 72 pixels per inch. Points are only important if you need to consider how the website will be printed out physically.

### Font Face
Using `@font-face` downloads fonts to users' browser. This allows for the usage of fonts that users might not have installed.
```css
@font-face {
    font-family: 'SomeFont';
    src: url('fonts/chunkfive.eot#iefix') format('embedded-opentype'),
         url('fonts/chunkfive.woff') format('woff"'),
         url('fonts/chunkfive.ttf') format('truetype'),
         url('fonts/chunkfive.svg#ChunkFiveRegular') format('svg');
}
p {
    font-family SomeFont, serif;
}
```
`format` specifies the file format of the source font file. Different browsers support different formats, but including both ttf/otf and svg should cover basically all of them. Font formats should be included in this order: eot, woff, tff/otf, svg.

Sites like https://fontsquirrel.com/fontface/generator can convert between font file formats, and can also generate `@font-face` rules for you since they can get very complicated.

Keep in mind that this will slightly increase the load time for the web page and may result in users seeing a brief FUOC/FUOT (flash of unstyled content/text). This can be mitigated by trimming unnecessary glyphs from the font file or using CDN that can deliver the font files faster.

It's also important that the font is licensed appropriately for use.

Open source fonts can be found on sites like...
* https://fontsquirrel.com
* https://fontex.org
* https://openfontlibrary.org
Some will only be licensed for personal (non-commercial) use though.

Commercial fonts that can be used for a fee can be found on sites like...
* https://typekit.com
* https://kernest.com
* https://fontspring.com

Google also hosts some fonts at https://google.com/webfonts

### Font Weight (Bold)
```css
.someClass {
    font-weight: bold;
}

/* Turns off bold font, just in case a rule needs to be overridden. */
.someOtherClass {
    font-weight: normal;
}
```

### Font Style (italics, etc)
```css
.someClass {
    font-style: italic;
}

/* Normal text that has been slanted. Actual italics put some accents on the letters. */
.someOtherClass {
    font-style: oblique;
}

.someNormalClass {
    font-style: normal;
}
```

A lot of times browsers won't find a provided italic version for a font, so they'll just put the normal font at a slant (oblique).

### Uppercase and Lowercase
```css
/* Should also use the "letter-spacing" property with this to help readability. */
.uppercaseClass {
    text-transform: uppercase;
}

.lowercaseClass {
    text-transform: lowercase;
}

/* Capitalizes the first letter of every word. */
.capitalizedClass {
    text-transform: capitalize;
}
```

### Underline and Strikethrough
```css
.underlineClass {
    text-decoration: underline;
}

.overlineClass {
    text-decoration: overline;
}

.strikethroughClass {
    text-decoration: line-through;
}

/* Flashes text on and off. Considered to be annoying. */
.blinkClass {
    text-description: blink;
}

.decorationsRemovedClass {
    text-description: none;
}
```

### Leading (pronounced "ledding")
Leading (pronounced "ledding") is a typography term that refers to the vertical space between text lines. The parts of letters that drop below the baseline (like the bottom part of "y") are called "descenders". The parts of letters that go above the baseline (like the top part of "h") are called "ascenders". Leading is the space between ascenders and descenders.

The CSS property `line-height` controls the height of the entire height of the text, so that would be from the descender up to the leading. `fone-size` refers to the height from the descender up to the ascender, so the difference between `line-height` and `font-size` is the leading.

Increasing `line-height` therefore increases the leading.
```css
p {
    line-height: 1.4em;
}
```

As general rule, the vertical space between lines should be greater than the space between words to help readability.

A value between `1.4em` and `1.5em` is good to start with. `line-height` is best expressed in units of `em` so it scales with text size.

### Letter and Word Spacing
"Kerning" refers to the space between each letter.

The CSS property `letter-spacing` controls the amount of space between each letter, and `word-spacing` controls the amount of space between each word. The value for each should be given in units of `em` to scale properly with text size. The value specified adds onto the space that's already specified in whatever font being used. Most fonts usually have a base value of `0.25em`.

```css
h1 {
    /* All-caps words usually need a bit more space. */
    text-transform: uppercase;
    letter-spacing: 0.2em;
}
```

## Alignment
### Horizontal Alignment
```css
.leftAlignedClass {
    text-align: left;
}

.rightAlignedClass {
    text-align: right;
}

.centerAlignedClass {
    text-align: center;
}

.justifyClass {
    text-align: justify;
}
```
Justify alignment forces each line to take up the whole width by putting and equal amount of space between the words. Not sure why anyone would want that though.

### Vertical Alignment
Vertical alignment does NOT align elements according to the invisible, omnipresent CSS box, although it does do that for the `<td>` and `<th>` elements.

Vertical alignment is used with `<img>`, `<em>`, or `<strong>` elements.
```css
.baselineClass {
    vertical-align: text-top;
}

.subClass {
    vertical-align: sub;
}

.superClass {
    vertical-align: super;
}

.topClass {
    vertical-align: top;
}

.textTopClass {
    vertical-align: text-top;
}

.middleClass {
    vertical-align: middle;
}

.bottomClass {
    vertical-align: middle;
}

.textBottomClass {
    vertical-align: text-bottom;
}

/* Can also take a numerical length, or percentage of line height. */
.lengthClass {
    /* vertical-align: 4px; */
    /* vertical-align: 10em; */
    vertical-align: 20%;
}
```

## Indent
The `text-indent` property indents the first line of text within an element.
```css
h1 {
    text-indent: 10em;
    /* text-indent: 20px; */
}

/*
    Moves the element far to the left off the screen, basically making it disappear.
    This is useful where we still want the heading for linking or webcrawler purposes,
    but want the element to be displayed by something other than the element itself (like an image).
*/
h2 {
    text-indent: -9999px;
}
```

## CSS3
### Drop Shadow
The `text-shadow` property can be used to add drop shadows to text.
```css
p.dropShadowClass {
    /*
        First arg is how far to the left/right the shadow should be.
        Second is how far up/down the shadow should be.
        Third is how much blur the shadow should have.
        Fourth is the shadow's color.
    */
    text-shadow: 1px 1px 0px #000000;
}
```

### First Letter/Line Selector
CSS3 adds the `:first-letter` and `:first-line` pseudo-elements which can select the first letter/line of a text element. Pseudo-elements are placed at the end of selectors.
```css
p:first-letter {
    font-size: 200%;
}

p:first-line {
    font-weight: bold;
}
```

Pseudo-elements behave as if every element they described are enclosed in hidden HTML tags.

### Styling Links
CSS3 also adds pseudo-classes which act as if an extra value is present in the `class` attribute for elements.

The `:link` and `:visited` pseudo-classes can be used to specify the look of visited/unvisited links.
```css
a:link {
    color: deeppink;
}

a:visited {
    color: black;
}
```

Whenever pseudo-classes are used, they should appear in the following order.
1. `:link`
1. `:visited`
1. `:hover`
1. `:focus`
1. `:active`

### User-responsive Styling
The `:hover` pseudo-class selects elements which the user is currently hovering over. This does nothing for touch screens since it's not possible to hover over anything on a touch screen.
```css
input.submit:hover {
    background-color: #665544;
}
```

The `:active` pseudo-class selects elements that are currently being clicked. Any changes are usually displayed pretty briefly since most users don't hold down the mouse button or tap very long to click something.
```css
input.submit:active {
    background-color: chocolate;
}
```

The `:focus` pseudo-class selects elements that are in focus. An element is in focus if it's ready to be interacted with, which usually happens if it has been clicked once.
```css
input.text:focus {
    color: #665544;
}
```
