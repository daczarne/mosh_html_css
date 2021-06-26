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

We can also apply transformations along the Z axis of our web page. Before doing so we must use the `perspective()` function to define a virtual space. For example, `transform: perspective(200px)` means that in our virtual space, the distance between the element and the viewer is 200px. If we want to apply the same perspective to all child elements of an element, then we use the `perspective` property of that element.

``` css
.container {
  perspective: 200px;
}
```

With the `translateZ()` function we can move objects closer to the viewer (by supplying a positive value) or farther away from the viewer (by supplying a negative value).

``` css
.box:hover {
  transform: perspective(200px) translateZ(50px);
}
```

If we need to change the point of origin of the transformation we use the `transform-origin` property. To it we need to supply two values: `x-offset, y-offset`. The values `0 0` mean top-left corner of the element, and `100% 100%` means bottom-right corner of the element.

``` css
.box:hover {
  transform: perspective(200px) translateZ(50px);
  transform-origin: 0 50%;
}
```

## Transitions

We use the `transition` property to animate one or more properties. With this we can create a smooth transition between one state and the other. To this property we need to supply the name of the property we want to transition and a duration that specifies how long it should take to go from one state of the property to the other. For example, with the code below we are telling the browser that is should take 0.5 seconds to transition from the `.box` state (the normal state of the element), to the rotated state of the element (which should trigger on hover).

``` css
.box {
  width: 100px;
  height: 100px;
  background-color: gold;
  transition: transform 0.5s;
}

.box:hover {
  transform: rotate(45deg);
}
```

We can also supply a time function to the `transition` property. The default is `linear` which means that the transition will progress at a linear rate (same number of pixes per unit of time). But we also have functions like `ease-in` (start slowly and speed up), `ease-out` (start fast and slow down). We can specify a custom curve using the `cubic-bezier()` function. We don't have to build this functions ourselves. We can use tools like [cubic-bezier.com](https://cubic-bezier.com) to do it.

``` css
.box {
  width: 100px;
  height: 100px;
  background-color: gold;
  transition: transform 0.5s cubic-bezier(0.23, 0.59, 0.79, 0.41);
}

.box:hover {
  transform: rotate(45deg);
}
```

Optionally, we can also specify a delay value. This will determine how long after the trigger is detected the animation will start. For example, the code below says that the animation should start 1 second after the user hovers over the box.

``` css
.box {
  width: 100px;
  height: 100px;
  background-color: gold;
  transition: transform 0.5s linear 1s;
}

.box:hover {
  transform: rotate(45deg);
}
```

We can also animate multiple properties by just adding the instructions separated by commas. For example, the code below says that when the user hovers over the element, both the `transform` property and the `background-color` should be transitioned from one state to another.

``` css
.box {
  width: 100px;
  height: 100px;
  background-color: gold;
  transition: 
    transform 0.5s linear 1s,
    background-color 0.7s ease-in 0.9s;
}

.box:hover {
  transform: rotate(45deg);
  background-color: dodgerblue;
}
```

## Animations

For more complex animations the `transition` property will not be enough. Here's when we use the `animate` property. These animations are built by defining the state of the element in different **keyframes**. The keyframes are defined using the `@keyframes` rule. After calling the rule we need to supply a name for our animation, and, in between braces, define the states of the element.

``` css
@keyframes identifier {
  /* Frames go here */
}
```

Inside the braces we define our frames. Each frame is identified by a percentage of time that should have elapsed since the start of the animation for the transformations to occur. For example, in the code below we are saying that at 0% of time elapsed (i.e. at the beginning) the scale should be 1 (that is, do nothing). After 25% of the animation duration has elapsed the element should scale up to 1.3 times its base size. We can define as many frames in as many intervals as we want.

``` css
@keyframes pop {
  0% {
    transform: scale(1);
  }

  25% {
    transform: scale(1.3);
  }

  50% {
    transform: rotate(45deg);
    background-color: tomato;
  }

  100% {
    transform: rotate(0);
  }
}
```

After we've defined our animation we need to use it. To do so, we need to supply the name of our animation to the `animation-name` property of the targeted element (the element we wish to animate). We also need to specify how long our animation should last (since are frames are defined as a percentage of time elapsed). To do so, we use the `animation-duration` property and supply a number of seconds.

``` css
.box {
  width: 100px;
  height: 100px;
  background-color: gold;
  animation-name: pop;
  animation-duration: 4s;
}
```

Other useful properties are:

- `animation-delay` to specify a number of seconds to wait before starting the animation. The default value is 0.
- `animation-iteration-count` to specify how many times the animation must run. The default is 1. If we want it to run forever, we set it to `infinite`.
- `animation-timing-function` to specify the timing function. Default is `linear`, but `ease-in`, `ease-out`, `ease-in-out`, and `cubic-bezier` are also available.
- `animation-direction` to control the direction of the animation. Default value is `normal` which plays the animation from the first frame to the last. But we can set it to `reverse` to play it from last frame to first frame.

We can also use the short hand property `animation` and pass all values there in the correct order.

## Reusable animations

We can make animations reusable by using classes. We can also use animations created by other people. Some of those can be found in [Animate.css](https://animate.style/).
