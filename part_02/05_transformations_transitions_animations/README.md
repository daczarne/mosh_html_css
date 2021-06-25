# Transformations, transitions, and animations

[Transformations](#transformations)  
[3D transformations](#3d-transformations)  
[Transitions](#transitions)  
[Animations](#animations)  
[Reusable animations](#reusable-animations)  

## Transformations

In CSS we have multiple functions for transforming elements:

- we use `rotate()` to rotate an element. The argument must be a number of `deg`rees. Positive values rotate it clockwise, and negative values rotate the element counter-clockwise.
- we use `scale()` to scale an element up or down. It's input should be a factor (no units). A value larger than 1 enlarges the element, and a value less than 1 shrinks it.
- we use `skew()` for tilting the element to the left of to the right. The value should be a number of `deg`rees. A positive number will skew left, a negative number will skew right.
- we use `translate()` for positioning the element on the screen. If we supply one value with a `px` unit, the element will move that number of pixels to the right. If the single value is negative, it will move left. If we add a second number, if positive it will move down, if negative up. This function is a short hand for `translateX()` and `translateY()`. 

To use a transformation we need to use the `transform` property to the elements selector. We can add transformations to the element itself, or to a pseudo class selector (like `:hover`).

``` css
.box:hover {
  transform: rotate(15deg);
}
```

We can pass more than one function to a selector. When doing so, keep in mind that the order of the functions matters.

``` css
.box:hover {
  transform: rotate(15deg) translateX(50px);
}
```

## 3D transformations

## Transitions

## Animations

## Reusable animations
