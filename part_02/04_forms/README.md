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

Inside the form we need to include one or more input fields, also called **form controls**. To generate controls we use the `<input>` element. Each input element must have a `type`. These include:

- `text` for creating text input fields.
- `email` for creating email inputs. This are different from plain text in the sense that the email input includes email validation.

Each input field must have a label to tell the user what he/she needs to input in the field. To create such labels we use the `<label>` element. In between the element tags we put the name of the field. Each label has a `for` attribute. This attribute is used to link the `<label>` element to its corresponding `<input>` element. To achieve this, the value of the `for` attribute of the `<label>` element must be the same as the `id` attribute of the `<input>` element.

``` html
<form>
  <label for="name">Name</label>
  <input id="name" type="text" />
</form>
```

To vertically align an input and its label we need to wrap the two together in a `<div>` element.

```html
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

## Text fields

## Data lists

## Drop-down lists

## Check boxes

## Radio buttons

## Sliders

## File inputs

## Grouping related fields

## Hidden fields

## Data validation

## Submitting the form
