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

### Static positioning

By default, the `position` property of all elements is set to `static`, which means that it's not positioned, they appear exactly in their normal position.

### Relative positioning

If we set its position to `relative` we can position the element relative to its normal (`static`) position. Now we can use properties like `top`, `left`, `bottom`, and `right` to move the element around. For example, setting `left: 5rem;` will move the element 5 rem units to the right (because it will add 5rem units of space to its left). We can also use negative values to move the element the other way.

Moving the elements around will sometimes cause overlapping. Which element will be displayed in front of which depends on the elements position in the DOM. The element that comes last in the DOM will appear in front of the elements that come before it in the DOM. We can modify this behavior by setting the `z-index` property. This property is by default set to 0, but we can change it to positive values to make elements come forward, or to a negative value to make elements move backwards.

```css
.boxes {
  border: 3px solid lightgrey;
}

.box-two {
  background-color: tomato;
  position: relative;
  left: 5rem;
  bottom: 2rem;
  z-index: 999;
}
```

### Absolute positioning

With absolute positioning we can position an element relevant to its container. To do so, we need to first set the position of the parent element to `relative`.

```css
.boxes {
  border: 3px solid lightgrey;
  position: relative;
}

.box-two {
  background-color: tomato;
  position: absolute;
  right: 0;
  bottom: 0;
  z-index: 999;
}
```

Whenever we position an element with an `absolute` positioning, that element is removed from the normal flow of the page. This means that other block-level elements that come after it will be pushed up. From the parent's point of view, that element does not exist.

## Fixed

With `fixed` position we can position elements relative to the viewport. These elements will never leave the viewport and will always be shown. This is very commonly used for things like nav-bars.

```css
.box-two {
  background-color: tomato;
  position: fixed;
  top: 0;
}
```

## Floating elements

We use the `float` property to build layouts. Setting the `float` property of an element to `left` cause that element to float to the left of its container. As a consequence, the subsequent elements will float around it.

If we want to clear the floating of subsequent elements, we need to set the `clear` property to the same value as the `float` of the previous element. So, if we set `float: left;` in an element, then we need to set `clear: left;` in the sibling element that we want to prevent from floating. We can set `clear` to `both` to clear both floats.

By default, parent elements don't see floated elements. This may cause **parent collapsing**. One way of solving this is to add an empty `<div>` at the end of the collapsed parent and set its `clear` property. The problem with this approach is that this `<div>` is not semantic. We can instead solve the problem by using pseudo-elements. We need to target the `::after` pseudo-element of the parent element that we want to avoid collapsing. This pseudo-element does not need content, but it does need to be changed to `display: block;` so that it becomes a block-level element, and we need to clear the float as well.

```css
.clear-fix::after {
  content: "";
  display: block;
  clear: both;
}
```

Another solution is to set the `overflow` property of the collapsed element to any value other than `visible`. But this might cause other problems with our layouts.

Because of all this issues the use of floats is now discouraged over the use of FlexBox or Grid layouts.

## FlexBox

### Elements layout

FlexBox is used for laying out elements in one direction: `row` or `column`. To use FlexBox we need to set the `display` property to `flex`. The container element will still be a block-level element, but it will behave according to Flex rules in the inside. By default, the orientation will be `row`.

We control the direction of elements with the `flex-direction` property. Default is `row`, but we can change it to `column`, `row-reverse`, or `column-reverse`.

To align elements in Flex we need to understand the **axis**. FlexBox has two axes that depend of the `flex-direction` property:

- **Main** will be the horizontal axis if the direction is row, or the vertical axis if the direction is column
- **Cross** will be the vertical axis if the direction is row, or the horizontal axis if the direction is column

![](img/flex_axes.png)

We use two properties in order to vertically and horizontally align items in FlexBox:

- `justify-content` is used to align items along the main axis
- `align-items` is used to align items along the cross axis

As we add more and more elements into the container, each element will become smaller and smaller while Flex tries to fix all elements in one row (or column). We can change this behavior using the `flex-wrap` property. Its default value is `nowrap`, but we can change it to `wrap` (amongst other possible values).

Now we can use the `align-content` property to align multiple lines (or even the entire content as a whole).

```css
.container {
  border: 3px solid lightgray;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  align-content: center;
  height: 90vh;
}
```

After we have built the layout of the container, we can layout its child elements. We can use the `align-self` property to move a child element to a different position inside the space assigned for it by the container.

``` css
.box-one {
  align-self: flex-start;
}
```

### Elements sizing

To size elements we use the following properties:

- `flex-basis` is used to set the initial size of a flex element. If we set the direction to `row`, then this property will targe the `width` property of the element, and, if direction is set to `column`, it will target the `height` property.
- `flex-grow` is used to set the growth factor of a flex element. The final size of elements is determined by adding all the growth factors and assigning each element the proportion of the available space that is equal to its contribution to the total growth factor.
- `flex-shrink` is used to set the shrink factor of a flex element. Same as before, but for shrinking elements.
- `flex` is a short hand property that combines all the previous ones (order is `flex-grow` `flex-shrink` `flex-basis`). If we supply a single value it will be used for the `flex-grow` property.

All these properties should be applied to flex elements, not to their container.

```css
.box {
  width: 5rem;
  height: 5rem;
  background-color: gold;
  margin: 1rem;
  flex-basis: 10rem;
  flex-grow: 1;
  flex-shrink: 0;
}

.box-one {
  align-self: flex-start;
  flex-basis: 5rem;
  flex-grow: 2;
  flex-shrink: 1;
}
```

## Grid

## Hiding elements

## Media queries
