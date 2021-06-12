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

## Measurement units

## Positioning

## Floating elements

## FlexBox

## Grid

## Hiding elements

## Media queries
