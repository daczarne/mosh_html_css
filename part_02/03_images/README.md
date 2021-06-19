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

If we have a page with multiple images, each time each user requests each image a request is sent to the server. We can use CSS Sprites to optimize these requests. We can combine all images into a single image and then get that image with a single HTTP request. To generate the sprites we can use any online sprite generator (like [here](https://www.toptal.com/developers/css/sprite-generator/)). The generator generates a `png` file with all our images and the CSS classes to use them.

Now we can add the images using `<span>` elements instead of `<img>` elements. The images are applied as a background image. Each span needs to have the class that matches the class in the CSS that corresponds to that image.

```html
<span class="bg-dishes"></span>
<span class="bg-landing"></span>
<span class="bg-rocketship"></span>
<span class="bg-saturn"></span>
<span class="bg-ufo"></span>
```

Don't include large images in sprites, only logos and icons.

## Data URLs

This is another optimization technique to reduce the number of HTTP requests. It's formerly known as Data URIs. Data is just another protocol that is used to represent a binary file as a sequence of characters. The data URI is passed as the `src` attribute of the `<img>` element. It starts with `data`, which is just the protocol. Then, separated by a colon `:`, comes `image/png` which specifies the type of data we are representing. After that comes a semi-colon `;`, followed by the actual data.

``` html
<img
  alt=""
  src="data:image/png;base64,a_whole_bunch_of_characters_here"
/>
```

Now the image is embedded into the HTML document. Therefore, the browser did not have to send an HTTP request to get it.

Problems with this approach include:

- size of the embedded code is always larger that the size of the original resource.
- increased complexity, as each data URL needs to be generated.
- slow on mobile.

## Clipping

In CSS we can easily clip, or cut, a part of an image. To do so we need to generate a clip path. One tool to produce such paths is [Clippy](https://bennettfeely.com/clippy/). This online tool will generate the value that we need to use for the `clip-path` property of the image element.

``` css
img {
  clip-path: polygon(0% 20%, 60% 20%, 60% 0%, 100% 50%, 60% 100%, 60% 80%, 0% 80%);
}
```

## Filters

In CSS we can add filters to our images like: `grayscale`, `blur`, `contrast`, `brightness`, and so on. All of the are implemented with a function that is passed to the `filter` property. For example, if we want to apply a 70% gray-scale filter we use:

```css
img {
  filter: grayscale(70%);
}
```

We can also apply more than one filter. To do so we just pass the different function one after the other:

```css
img {
  filter: grayscale(70%) blur(3px);
}
```

Filters can also be triggered by pseudo-classes like `:hover`.

```css
img:hover {
  filter: grayscale(70%) blur(3px);
}
```

A complete list of filtering functions can be found in the [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/filter).

## Supporting high-density screens

## Resolution switching

## Using modern image formats

## Art direction

## Scalable Vector Graphics (SVG)

## Font icons
