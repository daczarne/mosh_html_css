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


## Relational selectors


## Pseudo-class selectors


## Selectors specificity


## Inheritance


## Colors

## Gradients


## Borders

## Shadows

