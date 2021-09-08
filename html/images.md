# Images
Image files that are stored under the website's root directory can then be displayed on the website's pages using the `<img>` element.

`<img>` elements are empty elements, which means that there is no closing tag. The element must have the two attributes `src` and `alt`.

The value of the `src` attribute is the relative path to the image file.
```html
<!-- Example file structure
root_dir/
    images/
        donkeys.jpg
    index.html -->

<!-- index.html -->
<html>
    <body>
        <img src="images/donkeys.jpg" alt="a donkey" />
    </body>
</html>
```

The value of the `alt` attribute should be a text description of the image. This is useful for things like screen readers for the visually impaired and also for search engines. If the image is something just for formatting (a horizontal line, for example), the value of the `alt` attribute can just be the empty string.

The attribute `title` can also be used. The value of this attribute gets displayed as text when the user hovers over the image.

The attributes `height` and `width` can be used to specify the height and width of an image in number of pixels. It's becoming more common to specify the image size in CSS rather than HTML though.

## Image Placement
Where the `img` element appears in the code will affect how it appears on the web page.
```html
<html>
    <body>
        <!-- Image appears on own line and text starts underneath the image. -->
        <img src="pic.jpg" alt="pic" />
        <p>words words words words</p>

        <!-- Text starts after the image but on the same line. -->
        <p><img src="pic.jpg" alt="pic" /> words words words</p>

        <!-- Image is placed midway through the paragraph. -->
        <p>words words words<img src="pic.jp" alt="pic" /> words words</p>
    </body>
</html>
```

Block elements (like `p` and `h1`) always start a new line. Inline elements (like `b`, `em`, and `img`) sit within a block elements and don't start a new line.

## Horizontal Alignment
Prior to HTML5, the `align` attribute was used to control how parts of the page flowed around images. It has been removed in HTML5 in favor of using CSS.
```html
<html>
    <body>
        <!-- Text appears on the left side of image. -->
        <p><img src="pic.jpg" alt="pic" align="left" />words words words</p>

        <!-- Text appears on the right side of image. -->
        <p><img src="pic.jpg" alt="pic" align="right" />words words words</p>
    </body>
</html>
<!-- In this example, the text will flow right up to the edge of the image,
     making it a little hard to read. CSS can be used to add a little gap. -->
```

## Vertical Alignment
Again, the vertical alignment attributes are no longer in HTML as of HTML5.
```html
<html>
    <body>
        <!-- Text begins at the top of the image -->
        <p><img src="pic.jpg" alt="pic" align="top" />words words</p>

        <!-- Text begins at the middle of the image -->
        <p><img src="pic.jpg" alt="pic" align="middle" />words words</p>

        <!-- Text begins at the bottom of the image -->
        <p><img src="pic.jpg" alt="pic" align="top" />words words</p>
    </body>
</html>
<!-- In this example, the text will flow right up to the edge of the image,
     making it a little hard to read. CSS can be used to add a little gap. -->
```

To have the text wrap completely around the image, use `float` in CSS. Prior to HTML5, the same effect could be achieved with `align="left or right"`, but this is no longer valid.

## Figures (HTML5)
HTML5 introduces the `figure` element which allows for images to be associated with a caption.
```html
<html>
    <body>
        <figure>
            <img src="pic.jpg" alt="pic" />
            <figcaption>The caption for the image.</figcaption>
        </figure>
    </body>
</html>
```

Multiple images can be included in a `figure` element as long as it's ok for them all to have the same caption.
