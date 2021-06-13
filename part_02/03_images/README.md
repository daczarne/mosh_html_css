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
