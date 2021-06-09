# CSS

[Providing CSS](#providing-css)  
[Normalizing CSS](#normalizing-css)  
[Basic selectors](#basic-selectors)  
[Relational selectors](#relational-selectors)  
[Pseudo-class selectors](#pseudo-class-selectors)  
[Selectors specificity](#selectors-specificity)  
[Inheritance](#inheritance)  
[Colors](#colors)  
[Gradients](#gradients)  
[Borders](#borders)  
[Shadows](#shadows)  

## Providing CSS

There are three different ways of providing CSS:

1. Embedded stylesheets: these are created by adding a `<style>` element in the `<head>` of an HTML document. The problem with this approach is that all CSS declarations need to be re coded into each HTML document that makes up our site. This is a maintenance hell! It also violates *Separation of concerns*.
2. External stylesheets: these involve creating a separate `.css` file and linking it to the web page by adding a `<link>` element in the `<head>` of an HTML document. The `<link>` element takes two attributes. The first one is `rel`, which defines the relationship between the HTML document and the asset we are linking to (in this case `stylesheet`). The second one is `href`, which provides the path to the asset we are linking to.
3. Inline styles: these are created by specifying the `style` attribute of an HTML element. These style declarations should be avoided. Use classes and ids instead.

> Precedence of CSS declarations: inline >> embedded stylesheets >> external stylesheets.

## Normalizing CSS

Different Browsers render HTML differently. To address this issue we use [Normalize.css](https://necolas.github.io/normalize.css/).

## Basic selectors

In CSS we can select elements for styling by: type (HTML tag), class, ID, or attributes. A selector is the first word of a CSS declaration (the one before the braces, `{}`). IDs must be unique. Only one element in the entire HTML document can have a given ID. Classes, on the other hand, can be re-used in multiple elements.

``` css
/* Selection by tag */
HTMLelement {
  rules: here;
}
```

``` css
/* Selection by ID */
#elementID {
  rules: here;
}
```

``` css
/* Selection by class */
.className {
  rules: here;
}
```

We can also select based on attributes. To do so, we include the attribute in square brackets. If we want to select elements where the attribute is equal to a certain value, we pass that value.

``` css
/* Select all anchors with a target attribute */
/* The value does not matter here */
a[target] {
  rules: here;
}
```

``` css
/* Select all anchors with its target attribute set to _blank */
a[target="_blank"] {
  rules: here;
}
```

``` css
/* Select all anchors with its href set to https://google.com */
a[href="https://google.com"] {
  rules: here;
}
```

``` css
/* Select all anchors with its href containing the word google */
a[href*="google"] {
  rules: here;
}
```

``` css
/* Select all anchors with its href starting with https */
a[href^="https"] {
  rules: here;
}
```

``` css
/* Select all anchors with its href ends with .com */
a[href$=".com"] {
  rules: here;
}
```

``` css
/* Select all anchors with its href starting with https and ending with .com */
a[href^="https"][href$=".com"] {
  rules: here;
}
```

## Relational selectors

We can also select elements based on their relationship to other elements. We can create descendant selectors like so

```css
#products p {
  rules: here;
}
```

This will apply all rules to all the `<p>` elements inside the element with id `products`. This includes `<p>` elements that have the `products` element as an ancestor, but not directly (parent). If we only want to target *child elements* (that is, direct descendants) then we need to add a greater than sign in between them, like so: 

```css
#products > p {
  rules: here;
}
```

To target direct siblings we use a plus sign, like so:

```css
#products + p {
  rules: here;
}
```

If instead of direct siblings we want to target all siblings of the `products` element, we use a tilde, like so:

```css
#products ~ p {
  rules: here;
}
```

Relational selectors have the advantage of enabling us to write cleaner markup, since we don't need to define that many classes and IDs. Nevertheless, they have two draw backs:

- they are fragile, as they depend on the elements position on the DOM
- they are not as fast as basic selectors

## Pseudo-class selectors


## Selectors specificity


## Inheritance


## Colors

## Gradients


## Borders

## Shadows

