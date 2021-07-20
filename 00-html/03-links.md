# Links
By "links", I mean links to other web pages.

Links are created with the `<a>` element. Anything between the opening and closing tags is what the user can click on (the "link text"). The destination of the link is specified in the `href` attribute.
```html
<html>
    <body>
        <a href="https://google.com">Click me!</a>
    </body>
</html>
```

The value of `href` should be the full web address for the destination ("absolute URL").

If the element is linking to a page in the same site, the domain can be omitted from the `href` attribute value. This is known as a "relative URL".
```html
<html>
    <body>
        <a href="someLocalPage.html">Some local page</a>
    </body>
</html>
```

## Directory Structure
A website will usually organize its pages (HTML files) into some directory structure. This directory structure is used to resolve URLs for the website.

A website's pages will have some root directory which contains all the pages of the website either directly or in subdirectories.
```
Directory structure for bigyams.com
the_root_dir/
    index.html
    yams_of_the_month/
        index.html
        grading_criteria.html
```
In the above example, the URL `https://bigyams.com/yams_of_the_month/grading_criteria.html` would be valid and load a page. The URL `https://bigyams.com/yams_of_the_month/asdf.html` would not.

Each directory of a website must have an `index.html` file. This file gets displayed as a page if no specific page file is specified in the URL, and is referred to as that directory's "home page". The URL `https://bigyams.com` would load the `the_root_dir/index.html` page. The URLs `https://bigyams.com/yams_of_the_month` and `https://bigyams.com/yams_of_the_month/index.html` would load the same page.

## Relative URLs
As stated before, relative URLs are used to link to different pages from within the same website. The relative URLs are resolved against the directory structure for the website.
```
Directory structure for bigyams.com
the_root_dir/
    index.html
    yams_of_the_month/
        index.html
        grading_criteria.html
```
In the above example, if the root `index.html` had a link to the `yams_of_the_month` grading criteria page, the link would look like `<a href="yams_of_the_month/grading_criteria.html">Grading Criteria</a>`. If the page `yams_of_the_month/grading_criteria.html` had a link to the website home page, it would look like `<a href="../index.html">Home</a>`.

Relative URLs are relative to the path of the page that contains them. If the path starts with a `/` though, it's resolved starting from the root directory. The link `<a href="/">link</a>` would link to the home page for the whole site.

## Email Links
To create a link that will open up the user's default email program and address an email to some email address, use `mailto:` in the `href` attribute.
```html
<html>
    <body>
        <a href="mailto:somebody@somewhere.com">Email somebody</a>
    </body>
</html>
```

## Opening Links in a New Window
Add the `target=_blank` attribute to have the link open in a new window. Customarily, this is done whenever a link goes to some external site. Apparently opening links in new windows should generally be avoided in other cases, and the link text should notify the user that the link will open in a new window.
```html
<html>
    <body>
        <a href="https://external-site.com" target="_blank">External site (opens in new window)</a>
    </body>
</html>
```

## Linking to Sections of a Page
Linking to a specific part of a web page can be done by giving some element an `id` attribute with some value and then using that value in a URL. Using the URL will then jump to the element with the corresponding value for the `id` attribute. Every HTML element can have an `id` attribute. No two `id` attributes should have the same value on a single page. `id` attribute values should start with only either a letter or underscore.

To link to the section of the page, create an `<a>` element and set the `href` to a URL with the `id` value after `#` character. If the link is going to a page section on the same page, the `href` value can just be of the form `#id-value`.
```html
<html>
    <body>
        <h1 id="top">TOP</h1>
        <a href="#bottom">Jump to bottom</a>
        <p><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /></p>
        <p><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /></p>
        <p><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /></p>
        <p><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /></p>
        <p><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /></p>
        <p><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /></p>
        <p><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /></p>
        <p><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /></p>
        <p><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /></p>
        <p><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /></p>
        <a href="#top">Jump to top</a>
        <h1 id="bottom">BOTTOM</h1>
    </body>
</html>
<!-- The URL to link to a page section on an external page would be something like "https://domain.com#pagesection" -->
```
