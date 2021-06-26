# Writing clean and maintainable CSS

[CSS Best Practices](#css-best-practices)  
[Variables](#variables)  
[Object-oriented CSS](#object-oriented-css)  
[BEM](#bem)  

## CSS Best Practices

Eight techniques that will make your CSS more easy to read and maintainable

1. Follow a naming convention consistently (like *snake_case*, *camelCase*, *kebab-case*, *PascalCase*)
2. Create logical sections in your stylesheet. Split your CSS for large projects.
3. Avoid over specific selectors
4. Avoid the `!important` keyword
5. Sort CSS properties
6. Take advantage of style inheritance
7. Extract repetitive patters (use object-oriented CSS)
8. Avoid repetitive values (use variables)

## Variables

We use variables (also called custom properties) to keep our code DRY. Variables need to be declared at the top of our file in the `:root` pseudo-class selector. All variables start with two hyphens and then their name: `--var-name`, followed by colon, `:`, and their value. All elements in the DOM will have access to this custom properties.

``` css
:root {
  --color-primary: #ffdd36;
  --border-size: 2px;
  --border-radius: 10px;
}
```

Now we can access them using the `var()` function, and supplying the name of the variable as an argument.

``` css
.one {
  background: var(--color-primary);
}

.two {
  color: var(--color-primary);
}
```

## Object-oriented CSS

OO-CSS is based on two simple principles:

1. **Separate container from content**: This means that styles for the container and the content should not be declared together. This makes content styles reusable and avoids replication.
2. **Separate structure from skin**: rules that define the structure of a component (height, width, padding, margins, display, etc), should not be declared in the same rules that define the look of a component (color, background, fonts, etc). We can then apply multiple classes to elements when we want to use both rules. Use abstract names for classes.

## BEM

BEM is a popular naming convention. It stands for **Block Element Modifier**. A block is any modular component of our web page.

In BEM the name of the module and the name of the element are separated with two underscores. So, the class `card-header` becomes `card__header`.

The names of the block and the name of the modifier are separated using double dashes, `--`. So, the class `card_popular` becomes `card--popular`.
