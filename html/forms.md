# Forms
Forms are places on the page where the user can input data. These include things like text boxes, radio buttons, check boxes, submit buttons, etc.

Forms are specified with the `<form>` element.

The `<form>` element must always have the `action` attribute set. The value for the attribute should the URL of the page that should receive the form's data once submitted.

The `method` attribute specifies the sending method, which is always one of either `get` or `post`. If the method isn't specified the default is a get request.

Get requests have their parameters appended at the end of the URL, and are good for small requests. As an example, navigating to the URL `https://domain.com?param1=someValue&param2=someOtherValue` is the same thing as sending a get request to `domain.com` with the parameters `param1` and `param2` respectively set to `someValue` and `someOtherValue`.

Post requests send their data in HTTP headers, not the URL itself. Post requests are better suited for requests with large or private payloads.

The `id` attribute allows for useful identifier strings to be set on forms.

The `size` attribute should no longer be used. It was used in the past to set the width of text input forms. This should now be done using CSS.

Below is an example of the `<form>` element.
```html
<html>
    <body>
        <form action="https://server.com/formHandler" method="get">
            <p>This is where the form would appear.</p>
        </form>
    </body>
</html>
```
The `<form>` element isn't very useful though without some `<input>` elements specified.

## Input
The `<input>` element is used to create the actual input fields on the page. The type of input field that is created is controlled by the `type` attribute.

The `name` attribute controls the "key" that will be assigned to the value that is given to the input when the request is created.

### Single-line Text
When the `type` attribute is set to `text`, a single line text input field is created.

The `maxlength` attribute can also be used to limit the number of characters that can be entered into the field.

```html
<html>
    <body>
        <form action="https://somewhere.com">
            <p>
                Username:<input type="text" name="username" maxlength="5" />
            </p>
        </form>
    </body>
</html>
```

### Passwords
Set the `type` attribute to `password` to create a password input field. The password field is the same as the single-line text field, except the input characters are hidden.
```html
<html>
    <body>
        <form action="https://somewhere.com">
            <p>
                Password:<input type="password" name="password" />
            </p> 
        </form>
    </body>
</html>
```

The `maxlength` and `size` attributes can also be used on inputs of type `password`.

### Multi-line Text
The `<textarea>` element creates a text box that the user can use to specify multiple lines of text input.
```html
<html>
    <body>
        <form action="https://somewhere.com">
            <textarea name="myTextBox">Enter text here...</textarea>

            <textarea name="olderStyleTextBox" rows="4" cols="20">Enter text here...</textarea>
        </form>
    </body>
</html>
```

The initial size of `<textarea>` box can be controlled with the `rows` and `cols` attributes, but that is no longer best practice. Instead, CSS should be used. The units of `rows` and `cols` are in character height/width.

The element text given between the `textarea` tags are what will initially appear in the text box. To clear this automatically when the user selects the text box, use Javascript.

## Radio Buttons
Radio buttons are buttons that only allow at most one of them to be selected at any time.
```html
<html>
    <body>
        <form action="https://somewhere.com">
            <p>Please select one.
                <br />
                <input type="radio" name="choice" value="choice1" checked="checked"/>Choice 1
                <br />
                <input type="radio" name="choice" value="choice2" />Choice 2
                <br />
                <input type="radio" name="choice" value="choice3" />Choice 3
            </p>
        </form>
    </body>
</html>
```
The values for the attribues `name` and `value` are sent along in the request once the form is submitted.

The attribute `checked` indictes which button should be selected initially on page load. The value should always be `checked`. Only one of the radio buttons should have this attribute.

## Checkboxes
Checkboxes can be deselected without having to select another checkbox.
```html
<html>
    <body>
        <form action="https://somewhere.com">
            <p>Select all that apply.<br />
                <input type="checkbox" name="choices" value="choice1" checked="checked" />Choice 1<br />
                <input type="checkbox" name="choices" value="choice2" checked="checked" />Choice 2<br />
                <input type="checkbox" name="choices" value="choice3" />Choice 3
            </p>
        </form>
    </body>
</html>
```
Like the radio button, the values for the `name` and `value` attributes are sent along in the request once the form is submitted, and the `checked` attribute controls which checkboxes are checked initially. That value of the `checked` attribute should also always be `checked`.

## Dropdowns
Dropdowns (also called "select boxes") are those things that drop down a list of options when clicked and allows the user to select one of them.
```html
<html>
    <body>
        <form action="https://somewhere.com">
            <p>Select one from the dropdown.<br />
                <select name="choice">
                    <option value="choice1">Choice 1</option>
                    <option value="choice2">Choice 2</option>
                    <option value="choice3" selected="selected">Choice 3</option>
                </select>
            </p>
        </form>
    </body>
</html>
```
The values for the `name` and `value` attribute for the selection option will be sent along in the request once the form is submitted.

The `selected` attribute specifies which option will be selected on initialization. The value of this attribute should always be `selected`, and only one `option` element should have it specified.

## Multi-select Box
A multi-select box is the same as a drop down, except more than one option can be selected. Users will need to hold down shift/control/command while clicking in order to select more than one option though.

To create a multi-select box, add the `multiple` attribute with the value `multiple` to a `select` element.
```html
<html>
    <body>
        <form action="https://somewhere.com">
            <p>Select all that apply.<br />
                <select name="choices" multiple="multiple" size="2">
                    <option value="choice1">Choice 1</option>
                    <option value="choice2">Choice 2</option>
                    <option value="choice3">Choice 3</option>
                </select>
            </p>
        </form>
    </body>
</html>
```
The `size` element specifies how many options the box should be able to display at once. To see the rest of the options, the user will need to scroll down. The behavior of this attribute can be very inconsistent across browsers, so make sure to test thoroughly when using it.

## File Input Box
File input boxes allow users to upload local files.
```html
<html>
    <body>
        <form action="https://somewhere.com" method="post">
            <p>Upload file here.<br />
                <input type="file" name="user-file" />
            </p>
        </form>
    </body>
</html>
```
File upload forms must have a method of `post`.

## Submit Button
The submit button sends the form's data to the server specified in `action`.
```html
<html>
    <body>
        <form action="https://localhost">
            <p>Write a comment.</p><br />
            <textarea name="comment" /><br />
            <input type="submit" name="commentSubmit" value="Submit"/>
        </form>
    </body>
</html>
```
The `name` attribute on the submit button is completely optional.

The `value` attribute controls the text that will appear on the button itself.

## Image Button
To have an image act as the submit button, set the `type` attribute to `"image"`.
```html
<html>
    <body>
        <form action="https://localhost">
            <!-- The "src", "width", "height", and "alt" attributes all behave the
                 same as in the <img> tag -->
            <input type="image" src="dir/image.jpg" width="100" height="20"
                   alt="submit button image"/>
        </form>
    </body>
</html>
```

## Button and Hidden Controls
The `button` element allows for more control over how the submit button for a form appears.
```html
<html>
    <body>
        <form action="https://localhost">
            <!-- This button's appearance has both an image and text. -->
            <button>
                <img src="plus.jpg" alt="plus" width="10" height="10" />Add
            </button>
        </form>
    </body>
</html>
```

A hidden `input` element has its `type` attribute set to `"hidden"`. They're useful for adding more inputs to a form that the user doesn't need to see.
```html
<html>
    <body>
        <form action="https://localhost">
            <button>Click</button><br />
            <input type="hidden" name="extraValue" value="payload" />
        </form>
    </body>
</html>
```

## Labeling Form Controls
The `label` element should be used on all `input` elements of a form so that each input on the web page appears with a sensible label. This is also necessary to support vision-impaired users.
```html
<html>
    <body>
        <form action="https://localhost">
            <!-- The input is within the label element -->
            <label>Age: <input type="text" name="age" maxlength="3" /></label><br />

            <!-- The inputs are not within the label element, but the labels
                 have their "for" attribute set to the matching "id" value for
                 their appropriate "input". -->
            Gender:
                <input id="female" type="radio" name="gender" value="f" /><label for="female">Female</label>
                <input id="male" type="radio" name="gender" value="m" /><label for="male">Male</label><br />
            <input type="submit" />
        </form>
    </body>
</html>
```

## Grouping Form Elements
`form` controls can be grouped together inside the `fieldset` element.

Most browsers render the `fieldset` element as a box. The appearance can be controlled with CSS.

The `legend` element can be given as the first subelement of `fieldset` to add a visible caption.

```html
<html>
    <body>
        <form action="https://localhost">
            <fieldset>
                <legend>Contact</legend>
                <label>Email<br /><input type="text" name="email" /></label><br />
                <label>Phone<br /><input type="text" name="phone" /></label>
            </fieldset>
            <input type="submit" />
        </form>
    </body>
</html>
```

## HTML5
### Form Validation
Traditionally done by Javascript, form validation can now be done with just HTML if HTML5 is supported.

One example of form validation is the `required` attribute. This attribute prevents the form from being submitted if any inputs marked as `required` are empty.
```html
<html>
    <body>
        <form action="https://localhost">
            <!-- The value of the "required" attribute doesn't actually matter. -->
            <label>Username: <input type="text" required="required" /></label><br />
            <label>Password: <input type="text" required="required" /></label><input type="submit" />
        </form>
    </body>
</html>
```

### Specialized Inputs
HTML5 introduces specialized inputs for calendar dates, emails, etc. Some smartphones may optimized their keyboards depending on the input type (showing the `@` symbol for emails, etc.).

These specialized inputs also act as form validation and will block form submission if they detect malformed input.

Older browsers that don't support HTML5 will probably display these inputs as single line text boxes.
#### Date
```html
<html>
    <body>
        <form action="https://localhost">
            <label>Date: <input type="date" /></label><br />
            <input type="submit" /> 
        </form>
    </body>
</html>
```

#### Email
```html
<html>
    <body>
        <form action="https://localhost">
            <label>Email: <input type="email" /></label><br />
            <input type="submit" /> 
        </form>
    </body>
</html>
```

#### URLs
```html
<html>
    <body>
        <form action="https://localhost">
            <label>URL: <input type="url" /></label><br />
            <input type="submit" /> 
        </form>
    </body>
</html>
```

#### Search
This input doesn't automatically send the form to a search engine, but some browsers render the input differently if the type is set to `search`.
```html
<html>
    <body>
        <form action="https://localhost">
            <label>Search: <input type="search" /></label><br />
            <input type="submit" /> 
        </form>
    </body>
</html>
```

### Placeholder
Any HTML5 text input can have the `placeholder` attribute set to some text which will initially appear in the text input box. This text will disappear once the user selects the text input and starts typing.

Browsers that don't support HTML5 will simply ignore this attribute.

```html
<html>
    <body>
        <form action="https://localhost">
            <input type="text" placeholder="Type here..." />
        </form>
    </body>
</html>
```
