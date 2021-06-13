# Images

[Image types and formats](#image-types-and-formats)  
[Content images](#content-images)  
[Background images](#background-images)  
[CSS sprites](#css-sprites)  
[Data URLs](#data-urls)  
[Clipping](#clipping)  
[Filters](#filters)  
[Supporting high-density screens](#supporting-high-density-screens)  
[Resolution switching](#resolution-switching)  
[Using modern image formats](#using-modern-image-formats)  
[Art direction](#art-direction)  
[Scalable Vector Graphics (SVG)](#scalable-vector-graphics-svg)  
[Font icons](#font-icons)  

## Image types and formats

In computers we have two types of images:

1. **Raster** images are made up of pixels (photos)
2. **Vector** images which are defined by mathematical vectors (icons, logos)

Raster images can be computer-generated, but for the most part come from cameras. They use file extensions like `jpg`, `png`, `gif`, etc. Since they are made up of pixels, the larger the image, the larger the number of pixels and thus the larger the file size.

| Format | Colors | Transparency | Animation |
| :----: | :----: | :----------: | :-------: |
|  JPEG  |  16M   |      No      |    No     |
|  GIF   |  256   |     Yes      |    Yes    |
|  PNG   |  16M   |     Yes      |    Yes    |
|  WebP  |  16M   |     Yes      |    Yes    |

Vector images are computer-generated with software like Adobe Illustrator or other software that allows us to draw vectors. They are exported as `SVG` files. They always look sharp at any size (thus the Scalable is SVG).

## Content images

We add images in the HTML document with the `<img>` element. The `src` attribute is the path to the file. The `alt` attribute needs to be set to a description of the image which the browser will display if the image cannot be loaded, and screen readers will read this description. If the image is purely decorative of the page, then we set the attribute to empty, `alt=""`. If we don't include the attribute at all, then screen readers will read the file name, which might confuse the user.

By default, images are rendered at their real size. We can control the image size with the `width` and `height` properties.

## Background images

We can apply background images to elements. To do so, we can either use the `background` or `background-image` properties. We use the `url()` function to specify the path to the image.

```css
body {
  background-image: url("../images/bg-paper.jpg");
}
```

By default, the image will be repeated horizontally and vertically as many times as necessary to fill the viewport. This behavior is controlled by the `background-repeat` property. If we set it to `no-repeat` then the image will be shown once only at the top left corner. If we set it to `repeat-x` or `repeat-y` then the image will only be repeated along the horizontal or vertical axis respectively.

```css
body {
  background-image: url("../images/bg-paper.jpg");
  background-repeat: no-repeat;
}
```

To control the position of the image we use the `background-position` property. We need to pass two values: `horizontal-adjustment` and `vertical-adjustment`. These values can be either positive or negative. A positive `horizontal-adjustment` will move the image to the right, and a negative to the left. Likewise, a positive `vertical-adjustment` value will move the image up, and a negative down. It's usually recommended to use relative units. For example, 100% will move the image to the opposite side of its parent container (along the respective axis).

```css
body {
  background-image: url("../images/bg-paper.jpg");
  background-repeat: no-repeat;
  background-position: 100% -100%;
}
```

To control the size of the image, we use the `background-size` property and supply two values: `width` and `height`. If we set a value to 100% is will take up all the space in its container. Be aware the if we set the image height to 100% for an empty block-level container, it will disappear. This is because, by default, the height of a block-level element is the necessary hight to accommodate it's content, and since the container is empty, its height is zero. If we want the image to be a cover image (cover the entire container will keeping its aspect ratio), we can set this property to `cover`.

```css
body {
  height: 100vh;
  background-image: url("../images/bg-paper@2x.jpg");
  background-repeat: no-repeat;
  background-position: 100px 100px;
  background-size: cover;
}
```

We can make our background image stay fixed (relative to the viewport) while the content is scrolled by setting the `background-attachment` property to `fixed`. With this, the image will only be expanded to fill 100% of the viewport and it will not be stretched that much (or at all, depending on the image).

```css
body {
  height: 300vh;
  background-image: url("../images/bg-sanfrancisco.jpg");
  background-repeat: no-repeat;
  background-position: 100px 100px;
  background-size: 100% 100%;
  background-attachment: fixed;
}
```

## CSS sprites

## Data URLs

## Clipping

## Filters

## Supporting high-density screens

## Resolution switching

## Using modern image formats

## Art direction

## Scalable Vector Graphics (SVG)

## Font icons
