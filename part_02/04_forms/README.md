# Forms

[Creating a basic form](#creating-a-basic-form)  
[Styling forms](#styling-forms)  
[CSS Frameworks](#css-frameworks)  
[Text fields](#text-fields)  
[Data lists](#data-lists)  
[Drop-down lists](#drop-down-lists)  
[Check boxes](#check-boxes)  
[Radio buttons](#radio-buttons)  
[Sliders](#sliders)  
[File inputs](#file-inputs)  
[Grouping related fields](#grouping-related-fields)  
[Hidden fields](#hidden-fields)  
[Data validation](#data-validation)  
[Submitting the form](#submitting-the-form)  

## Creating a basic form

To create forms we use the `<form>` element. Each form must have an `action`, either `GET` or `POST`. This will be covered in the [Submitting the form](#submitting-the-form) section.

Inside the form we need to include one or more input fields, also called **form controls**. To generate controls we use the `<input>` element. Each input element must have a `type` (like `text` for creating text input fields, or `email` for creating email inputs with email validation).

Each input field must have a label to tell the user what he/she needs to input in the field. To create such labels we use the `<label>` element. In between the element tags we put the name of the field. Each label has a `for` attribute. This attribute is used to link the `<label>` element to its corresponding `<input>` element. To achieve this, the value of the `for` attribute of the `<label>` element must be the same as the `id` attribute of the `<input>` element.

``` html
<form>
  <label for="name">Name</label>
  <input id="name" type="text" />
</form>
```

To vertically align an input and its label we need to wrap the two together in a `<div>` element.

``` html
<form>
  <div>
    <label for="name">Name</label>
    <input id="name" type="text" />
  </div>
  <div>
    <label for="email">Email</label>
    <input id="email" type="email" />
  </div>
</form>
```

In order for the user to be able to submit the form, we need to add a submit button to it. To do so, we use the `<button>` element. We must supply a `type` attribute for each button. To make it a submit button, we use the `type="submit"` attribute. We can also add a button that clears out the form by adding a second button with `type="reset"` attribute. In general, these buttons are added at the bottom of the form, but as long as they are between the `<form>` tags, they'll work as expected.

``` html
<form>
  <div>
    <label for="name">Name</label>
    <input id="name" type="text" />
  </div>
  <div>
    <label for="email">Email</label>
    <input id="email" type="email" />
  </div>
  <button type="submit">Register</button>
  <button type="reset">Clear</button>
</form>
```

## Styling forms

To make the input field appear in a new line below its label, we can change the `display` property of the label from inline, to block.

## CSS Frameworks

Styling all elements in a form can be very time consuming. This is why we use CSS frameworks like Bootstrap. A framework is basically a library of CSS styles that we can re-use.

To implement Bootstrap we need to add the CND links in the `<head>` section of the HTML document.

``` html
<head>
  <link
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/css/bootstrap.min.css"
    rel="stylesheet"
    integrity="sha384-+0n0xVW2eSR5OomGNYDnhzAbDsOXxcvSN1TPprVMTNDbiYZCxYbOOl7+AMvyTG2x"
    crossorigin="anonymous"
  />
  <script
    src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/js/bootstrap.bundle.min.js"
    integrity="sha384-gtEjrD/SeCtmISkJkNUaaKMoLD0//ElJ19smozuHV6z3Iehds+3Ulb9Bn9Plx0x4"
    crossorigin="anonymous"
  ></script>
</head>
```

To style our form we now need to add the necessary classes. To do so, go to the [Forms](https://getbootstrap.com/docs/5.0/forms/overview/) section in the documentation. Here you can find different styles and the mark-up that you need to use in order for your page to look like it.

Another framework is [Milligram](https://milligram.io/). Just like Bootstrap, in order to use Milligram you first need to add the CND link to the `<head>` section of the HTML document. Milligram will provide basic CSS styling without you adding any classes (which means that the theme targets the HTML element tags).

``` html
<head>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/milligram/1.4.1/milligram.css">
</head>
```

## Text fields

Text fields are used to let the user input free text. We create them with the `<input>` element with the `type="text"` attribute.

``` html
<form>
  <label for="text-input">Text Input</label>
  <input id="text-input" type="text" />
</form>
```

We can change `type="number"` to transform it into an numeric input field. This will add up and down arrows to the side of the input field. If the user is on mobile, the number pad will come up when tapping on it.

``` html
<form>
  <label for="number-input">Numeric Input</label>
  <input id="number-input" type="number" />
</form>
```

We can also use `type="password"` to create password input fields. Whatever the user inputs here will be masked with dots.

``` html
<form>
  <label for="password-input">Password</label>
  <input id="password-input" type="password" />
</form>
```

If we change to `type="date"` our field becomes a date input selector.

``` html
<form>
  <label for="date-input">Date</label>
  <input id="date-input" type="date" />
</form>
```

If we set `type="email"` we get an input that looks like text, but has basic email validation.

``` html
<form>
  <label for="email-input">Email</label>
  <input id="email-input" type="email" />
</form>
```

You can see a complete list of all possible values in the [Mozilla documentation](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input).

When we want to allow the user to input multiple lines of text we use the `<textarea>` element. We use the attributes `cols` and `rows` to control the number of columns (characters per line) and rows (number of lines) that the user can input.

``` html
<form>
  <label for="textarea-input">Text area input</label>
  <textarea name="" id="textarea-input" cols="30" rows="10"></textarea>
</form>
```

If don't want the user to be able to re-size the text area box, we need to add the following rule to our CSS

``` css
textarea {
  resize: none;
}
```

The `<input>` element has other useful attributes:

- we use the `value="some_text"` attribute to pre-populate a field. We generally do this when we want to suggest an input for the user.
- we use the `placeholder="some_text"` attribute to provide an explanation text or example. This placeholder text disappears when the users inputs a value in the field.
- if we add the boolean attribute `readonly` then the user will not be able to change the `value` in the field. When submitted, this value will be sent to the server.
- if we add the boolean attribute `disabled` then the field will be grayed-out and the user will not be able to input anything. `value`s in a `disable`d field will not be sent to the server when submitting a form.
- `maxlength="number"` is an attribute that allows us to control the maximum number of characters the user is able to input in the field.
- we use the boolean attribute `autofocus` to cause the browser to focus on that field as soon as the page loads.

The `<textarea>` element has the same attributes except for the `value` one. If we want to pre-populate the element we need to provide the text in between the tags.

## Data lists

To provide the user with input suggestions as he/she types in the text input field, we need to add a `<datalist>` after the input field. This datalist must be linked to the input field. To do this, we need to provide a unique `id` to the datalist. Then, we pass the same value as the datalist `id` to the `<input>`'s `list` attribute. The user is still able to supply any text he/she wants into the field.

Inside the data list we need to provide a the list of `<option>`s that we want the user to select from. The text that the user will see in the selection list needs to be supplied in between the `<option>` tags. The value that is sent to the server when the form is submitted needs to be provided in the `value` attribute of each `<option>` element. By default, the browser will display both the `value` and the text.

Generally when using data lists we want to turn off the autocomplete feature of the browser for that input. To do so, we need to add the `autocomplete="off"` attribute to the `<input>` field.

``` html
<form>
  <div>
    <label for="text-input">Text Input</label>
    <input
      id="text-input"
      type="text"
      list="list-of-options"
      autocomplete="off"
    />
    <datalist id="list-of-options">
      <option value="option-1">Option 1</option>
      <option value="option-2">Option 2</option>
      <option value="option-3">Option 3</option>
      <option value="option-4">Option 4</option>
      </datalist>
  </div>
</form>
```

## Drop-down lists

To create a drop-down list we use the `<select>` element. We use its `id` attribute to link the element to a specific `<label>` element, and we use its `name` attribute when submitting the form to a server. If we add the boolean attribute `multiple` the user will be able to select multiple elements from the dropdown.

Inside the `<select>` element we can add multiple `<option>` elements. If we leave the first option empty the selection becomes optional for the user. He/She can choose not to select anything. If we add the boolean attribute `selected` to an option, that option becomes the default selection in the drop-down list.

``` html
<form>
  <div>
    <label for="drop-down-list">Drop-down list</label>
    <select name="" id="drop-down-list">
      <option value="option-1" selected>Option 1</option>
      <option value="option-2">Option 2</option>
      <option value="option-3">Option 3</option>
      <option value="option-4">Option 4</option>
    </select>
  </div>
</form>
```

If we have many `<select>` elements its better to group them together. To do so we use the `<optgroup>` element.

``` html
<form>
  <div>
    <label for="drop-down-list">Drop-down list</label>
    <select name="" id="drop-down-list">
      <optgroup label="group-1">
        <option value="option-1">Option 1</option>
        <option value="option-2">Option 2</option>
      </optgroup>
      <optgroup label="group-2">
        <option value="option-3">Option 3</option>
        <option value="option-4">Option 4</option>
      </optgroup>
    </select>
  </div>
</form>
```

## Check boxes

To generate check boxes we use the `<input>` element with a `type="checkbox"` attribute. To associate the box with its label we use the `<label>` element and set the `<input>` element's `id` attribute to the same value as the `<label>` element's `for` attribute.

``` html
<input type="checkbox" name="value-sent-to-server" id="checkbox-input" />
<label for="checkbox-input">Label</label>
```

To make a checkbox appeared selected by default we add the boolean attribute `checked` to the `<input>` element.

``` html
<input type="checkbox" name="value-sent-to-server" id="checkbox-input" checked />
<label for="checkbox-input">Label</label>
```

Likewise, if we want a checkbox to appear disabled (grayed-out) we need to add the `disabled` boolean attribute to the `<input>` element.

``` html
<input type="checkbox" name="value-sent-to-server" id="checkbox-input" disabled />
<label for="checkbox-input">Label</label>
```

## Radio buttons

When we want the user to select one out of a few options, we can use Radio Buttons. To do so we use the `<input>` element with `type="radio"`. When doing so, the `name` attribute is used to group multiple buttons (of which, the user will only be allowed to select one). As with check boxes before, to link a radio button with a label we supply the same value to the `<input>` element's `id` attribute than to the `<label>` element's `for` attribute.

``` html
<input type="radio" name="group-of-radio-buttons" id="radio-input-1" />
<label for="radio-input-1">Value shown to the user</label>
```

Here to we can pre-select by adding the `selected` boolean attribute, or disable by adding the `disabled` boolean attribute to the `<input>` element.

## Sliders

To generate slider inputs we use `<input>` element with a `type="range"`. We need to provide a `min`, `max`, and `value` attributes for the minimum value, maximum value, and currently selected value respectively.

``` html
<input type="range" min="0" max="100" value="90" />
```

To show the currently selected value to the user, we need to use JavaScript.

## File inputs

To allow the user the input files in forms (like when adding a profile picture that is saved in a raster image on the user's local computer) we use the `<input>` element with `type="file"`. This will generate a *Choose files* button and open the file explorer when clicked.

``` html
<input type="file" />
```

If we add the `multiple` boolean attribute, the user will be allowed to select multiple files.

``` html
<input type="file" multiple />
```

If we add the attribute `accept` we can specify the type of files the user can select. To add multiple file types we list them separated with a comma. We can also use wild-card selectors. For example, with `accept="image/*"` we allow the user to select any image file. Other options include `accept="video/*"` and `accept="audio/*"`.

``` html
<input type="file" accept=".jpg, .png" />
<input type="file" accept="image/*" />
```

## Grouping related fields

As our forms become larger and more complex we need to group together locally related form controls. To do so we use the `<fieldset>` element. Inside the `<fieldset>` element first we add a `<legend>` element to supply a title to the set, and then we add the form controls. Alternatively, we can use the `<section>` element to group, and an `<h2>` element to provide a title.

``` html
<form>
  <fieldset>
    <legend>Group 1</legend>
    <input type="text" name="" id="">
    <input type="text" name="" id="">
    <input type="text" name="" id="">
  </fieldset>
  <fieldset>
    <legend>Group 2</legend>
    <input type="text" name="" id="">
    <input type="text" name="" id="">
    <input type="text" name="" id="">
  </fieldset>
</form>
```

## Hidden fields

Sometime we need to create forms for editing content. When these forms are submitted to the server, the server has no way of knowing which element id in it's data base it should edit. This is were the hidden elements come to play. To create a hidden field we use the `<input>` element with `type="hidden"`. In the `name` attribute we supply the table column that the server needs to update, and in the `value` attribute the id of the entry.

``` html
<input type="hidden" name="table-column-name" value="id" />
```

Never store sensitive data in this inputs. Even though they are not rendered to the page, the user can still see them when using DevTools. We only use hidden fields to provide a server with the id of the content that is being edited.

## Data validation

Before submitting a form we must always validate the data to protect ourselves from data corruption and attacks. Some basic validation can be performed with HTML, but for more complex things we need to use JavaScript.

One attribute that we can use for data validation is the `required` boolean attribute. This make a field mandatory. We can also use `minlength` and `maxlength` to control how long a string can be. `maxlength` is an attribute that we should always use to prevent SQL injections.

``` html
<form>
  <input type="text" required minlength="3" maxlength="10" />
  <button type="submit">Submit</button>
</form>
```

If the field is for entering emails make sure to select the `email` type as this will cause the browser to check that the input is indeed an email.

``` html
<form>
  <input type="email" required />
  <button type="submit">Submit</button>
</form>
```

For numeric fields we can use the `min` and `max` attributes to make sure the value falls withing that range. This is very important when values must fall withing certain range (for example, a price cannot be negative).

``` html
<form>
  <input type="number" required min="0" max="10" />
  <button type="submit">Submit</button>
</form>
```

## Submitting the form

To allow form submission we need to include a *Submit* button. We can either add it with the `<button>` element, or with the `<input>` element of `type="submit"`. The difference between these two approaches is that with the `<input>` element we cannot add an icon.

``` html
<input type="submit" value="Submit" />
<button type="submit">Submit</button>
```

When submitting form there are two attributes that we need to consider: `action`, and `method`. The value of the `action` attribute is the backend service (a URL) to which the form needs to be submitted. The value of the `method` attribute is either `GET` or `POST`:

- we use `GET` when we want the form values to be appended to the target URL. We use it when we want to bookmark that URL so that we can get back to it.
- we use `POST` when we want the form values to be included in the body of the HTTP request.

To submit a form each `<input>` element must have a `name` attribute.
