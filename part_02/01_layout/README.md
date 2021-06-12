# Layout

[The box model](#the-box-model)  
[Sizing elements](#sizing-elements)  
[Overflowing](#overflowing)  
[Measurement units](#measurement-units)  
[Positioning](#positioning)  
[Floating elements](#floating-elements)  
[FlexBox](#flexbox)  
[Grid](#grid)  
[Hiding elements](#hiding-elements)  
[Media queries](#media-queries)  

## The box model

Whenever the browser renders an element it places it inside an invisible box. At the core of the box is the **content area**. This is were the elements content goes. Outside the content area we have the **padding**. This is the space between the content area and the **border** of the box. Around each box we have the **margin**.

![](img/box_model.png)

We can use the CSS property `padding` to control the padding. This property takes up to 4 values that work the same way as the border property seen before. The same holds for the `margin`. But keep in mind that the browser will collapse the margins of elements that are next to each other, while it will not collapse the padding. Therefore, to avoid issues:

- use padding to separate the content and the border
- use margin to separate elements from each other

## Sizing elements

The width and height properties are applied to the content area. If we add padding or borders the total size of the element will increase. The margin property does not impact the size of the visible box as it relates to the space between elements.

This behavior is controlled by the `box-sizing` property. By default it's set to `content-box`. But if we set it to `border-box` the `height` and `width` properties will be applied to the `border-box` (that is, the padding and the border space will be included in there). With this, the values that we provide for border and padding will be subtracted from the `height` and `width` properties before calculating the content area. In general, the `box-sizing` property will be included in the universal selector `*`. This rule does not apply to pseudo-elements. To do so, we need to explicitly include them.

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

The `width` and `height` properties are only applied to block-level elements. Inline elements will not use them. To make them use it we need to set their `display` property to `inline-block`.

## Overflowing

Overflowing happens when the content of an elements doesn't fit inside the element. We can control it with the `overflow` property. By default, it's set to `visible`. If we change it to `hidden` the part of the content that overflows the container will not be seen. We can also set it to `scroll` to get a horizontal and vertical scroll bar in the container element. We can set the `overflow` property to `auto` to make the scroll bars only appear if there's overflow.

The `overflow` property is a short hand for `overflow-x` and `overflow-y`. We can set them separately if we want the *x* and *y* axis to have different behaviors. Or, we can supply two values to the `overflow` property which the browser will apply to x and y respectively.

## Measurement units

In CSS there are multiple units of measurement. They fall in either one of two categories: **absolute**, o **relative**. Absolute units are always fixed, while relative unites depend on something else. For example, percentages are relative to the size of the elements container (its parent element).

|    Absolute     |       Relative       | Relative to ...                      |
| :-------------: | :------------------: | :----------------------------------- |
|   px (pixel)    |    % (percentage)    | the size of the container            |
|   pt (point)    | vw (viewport width)  | the viewport                         |
|    in (inch)    | vh (viewport height) | the viewport                         |
| cm (centimeter) |          em          | the font size of the current element |
| mm (millimeter) |         rem          | the font size of the root element    |

`pt`, `in`, `cm`, and `mm` are mostly used for printing and have no real application for the web. We should use `px` when we don't want the size of something to change. With relative units, the size of our elements will change as the size of the element that determines their size changes.

By default, block-level elements have a width of 100% and a height of 0%. If there's content inside the element, the height will increase to fit the content.

For `em` and `rem` keep in mind that if no parent element has a font size, the font size of the `html` element will be used. By default, browsers give the `html` element a `font-size` of `16px`. So, a width of `10em` means 10 times the font size of the current element. On the other hand, `rem` will multiply based on the font size of the root element. This means that we don't have to trace back inheritance, the size will always be based on the `font-size` of the `html` element.

## Positioning

## Floating elements

## FlexBox

## Grid

## Hiding elements

## Media queries
