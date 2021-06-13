# Typography

[Styling fonts](#styling-fonts)  
[Embedding web fonts](#embedding-web-fonts)  
[Flash of unstyled text](#flash-of-unstyled-text)  
[Font service](#font-services)  
[System font stack](#system-font-stack)  
[Sizing fonts](#sizing-fonts)  
[Vertical spacing](#vertical-spacing)  
[Horizontal spacing](#horizontal-spacing)  
[Formatting text](#formatting-text)  

## Styling fonts

Generally speaking there are three family fonts:

- **Serif** includes Georgia and Times New Roman
- **Sans-serif** includes Avenir, Arial, Futura, Helvetica, Roboto
- **Monospace** includes Consolas, Courier, Ubuntu

We define the font with the `font-family` property. VS Code will automatically recommend a **Font stack** based on Web safe fonts. These are font families that are generally available in computers. The browser will check if the first font in the stack is available in the users computer. If it is, it will use it. If it's not, it will fall back to the next font in the stack. The last in the stack is a generic font. Which one will actually be used will vary form one computer to another depending on what's installed on that computer/device. We usually define the `font-family` in the `body` element and let other child elements inherit it.

```css
body {
  font-family: Arial, Helvetica, sans-serif;
}
```

To set the *boldness* of the font we use the `font-weight`property. This can take a value (from 100 to 900) or a keyword value (with normal = 400, bold = 700, and so on).

```css
p {
  font-weight: bold;
}
```

To italicize the text we use the `font-style` property. Other values are available too. The default value of this property is `normal`.

```css
p {
  font-style: italic;
}
```

We control the size of the font with the `font-size` property. This property takes as value a keyword or a value, which can be absolute or relative values.

```css
p {
  font-size: 1rem;
}
```

To control the color of the font we use the `color` property. Any valid CSS color can be supplied here.

```css
p {
  color: #333;
}
```

## Embedding web fonts

We can add newer, better fonts to our websites. You can get free fonts from [Font Squirrel](https://www.fontsquirrel.com/). We can download the font files is `TTF`, `OTF`, `EOT`, `WOFF`, or `WOFF 2.0` depending on the font. For web it's better to use `WOFF` or `WOFF 2.0` since they are more compressed.

Once we have a font in our project we need to register it in at the top of the stylesheet with `@font-face` rule. This rule tells the browser everything it needs to know about how to use the fonts. The `font-family` rule here defines the name with which we are going to reference the font. The `src` property provides URLs to the fonts with their format. The `font-weight` and `font-style` properties are used to specify the values that the styling rules must have in order for that font to be used. For example, if the user makes a rule with `font-family: 'opensans'`, `font-weight: bold`, `font-style: normal`, then the browser will use the font located that the URL provided in the `src` property.

```css
@font-face {
  font-family: "opensans";
  src: url("../fonts/open-sans/opensans-bold-webfont.woff2") format("woff2"),
    url("../fonts/open-sans/opensans-bold-webfont.woff") format("woff");
  font-weight: bold;
  font-style: normal;
}
```

Once we've registered our fonts, we can add them to our font stack.

```css
body {
  font-family: "opensans", Arial, Helvetica, sans-serif;
}
```

## Flash of unstyled text (FOUT)

FOUT is a problem that users may encounter with our web sites assets if they are on a slow connection. Assets like fonts may take a long time to download and be installed on the users computer. While this is happening the browser will fallback to another font in the font-stack and this might cause some elements to not render correctly. We cannot fully avoid this problem. But we can use the `font-display` property in our `@font-face` declaration rule to minimize the problem.

By default, this property is set to `auto`. This lets the browser decide what should be done while the font is being downloaded. But this behavior is different from one browser to another. If we change it to `swap` all browsers will first render the text with a fallback font, and swap it with our font when it becomes available.

Another option is to set it to `fallback`. This will tell the browser that if the font is not available, then it should immediately fallback to another font in the stack.

A value that we should never use is `block`. This will cause the browser to not display the text until the font is available. The problem is that if the font never becomes available, then the text will never be displayed.

Lastly, we can set it to `optional`. With this value the browser will try to download the font and save it on cache. This can lead to the situation in which the text is rendered differently between the first and subsequent page visits.

## Font service

The largest free web font service is [Google Web Fonts](https://fonts.google.com/). Once we've made our selection, we grave the `<link>` elements and include them in the `<head>` of our HTML document. The first of them is telling the browser that it needs to make a connection with the domain specified in the `href` attribute, and retrieve content from there. The second one is a URL to a stylesheet.When we use font services, the fonts are not stored in our services, but retrieved from a third party host. The stylesheet has all the `@font-face` rules the browser needs to import the fonts.

```html
<link rel="preconnect" href="https://fonts.gstatic.com">
<link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&family=Roboto:wght@700&display=swap" rel="stylesheet">
```

The link URL has the query parameter `display=swap`. We can change this parameter here.

```html
<link rel="preconnect" href="https://fonts.gstatic.com">
<link href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&family=Roboto:wght@700&display=optional" rel="stylesheet">
```

## System font stack

With this stack we can tell the browser to use the default font of the users operating system. This can boost performance since no fonts need to be downloaded and mitigates the probability of having FOUT. The problem is that different OS use different default fonts. To use the system font stack we just pass it as the value of the `font-family` property.

```css
body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}
```

## Sizing fonts

We should not set font sizes in pixels because they vary between devices. In general, the main text of our page should be set to `1rem`. That means, one time the size of the font of the root element (the `<html>` element). If we don't have a CSS rule for the `html` element, the size will be set by the user's browser. This is usually set in the `body` rule.

```css
body {
  margin: 10px;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  font-size: 1rem;
}
```

We can then change the size of different elements as needed. For example, we can make our headings larger.

```css
h1 {
  font-family: Roboto, Arial, Helvetica, sans-serif;
  font-size: 2rem;
}
```

Since we are using a mobile first approach, this will be the values for mobile devices. For tablets and desktops, we want to use a media query to make them larger still. Because we are using relative font sizes, we only need to change the base from which they are calculated. this can be done by changing the `font-size` property in the `html` rule.

```css
@media screen and (min-width: 400px) {
  html {
    font-size: 130%;
  }
}
```

We can use services like [Type-Scale](https://type-scale.com/) to help us choose the font sizes.

## Vertical spacing

When building pieces of text we need to follow the **Law of proximity**. This means that humans will interpret content that is placed closer to each other as related. So our headings need to be closer to their text than to paragraphs that came before them. To control this, we use the `margin` property. As a rule of thumb, the top margin should be greater than the bottom margin.

To improve readability we use the `line-height` to generate space between lines. As a general rule of thumb, line height should be 1.5 times the font size. If we supply a value without a unit, the browser will multiply the `line-height` value times the `font-size` value and our design won't break if we change the `font-size` property.

```css
body {
  margin: 10px;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  font-size: 1rem;
  line-height: 1.5;
}
```

## Horizontal spacing

To control the spacing between letters in a text we use the `letter-spacing` property. To set letter spacing we shouldn't use relative values as this will push letter further and further apart when the font size changes. We use instead `px` values. By default this value will be set to 0, meaning that the base spacing of the font will be used. We need to set this value to a positive number if we want to increase the spacing, or a negative value if we seek to reduce it.

Likewise, we can specify the space between words with the `word-spacing` property.

``` css
body {
  margin: 10px;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  font-size: 1rem;
  line-height: 1.5;
  letter-spacing: 1px;
  word-spacing: 5px;
}

h1 {
  font-size: 4.209rem;
  margin: 3rem 0 1rem;
  letter-spacing: -1px;
}
```

The ideal line length should be between 50 and 70 characters. To control this we need to set the `width` property of the `<p>` object. The unit of measurement that we use here is `ch`. This is a unit that is relative to the width of the zero character. So, for example, `width: 50ch;` means that the width of the paragraph should be the same as the width of 50 zeros placed next to each other.

```css
p {
  width: 50ch;
}
```

## Formatting text

For controlling the horizontal alignment of the text we use the `text-align` property of the `<p>` element. Its default value is `left`. This is considered to be the best alignment for the web.

```css
p {
  text-align: left;
}
```

For adding indentation to the first line of a paragraph we use the `text-indent` property of the `<p>` element. This property takes a unit value, generally set in `rem`. To avoid indenting the first paragraph after a heading we need to use relational selectors. We could, for example, select a `p` that comes after another `p`.

```css
p + p {
  text-indent: 1rem
}
```

To decorate our text (underline, line-through, etc.) we use the `text-decoration` property of the `<p>` element. We also use this property to change how `<a>` links are styled.

```css
a {
  text-decoration: none;
}
```

To convert text to lower or uppercase we can use the `text-transform` property. If we set it to `capitalize`, it will capitalize the first letter of every word. This is sometimes used for headings.

```css
h1 {
  text-transform: capitalize;
}
```

To control white space we use the `white-space` property. If, for example, we set it to `nowrap` our text will always be displayed in one single line. This will cause horizontal scrolling. To control how our overflow is managed we can use the `overflow` property (for example, setting it to `hidden` will hide text that would otherwise be outside the `<p>` element). To change the ending of the visible text we can use the `text-overflow` property. For example, if we set `text-overflow: ellipsis` then an ellipsis will be shown when text is truncated due to overflow.

```css
p {
  width: 50ch;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
```

We can also use the `line-clamp` property to truncate text based on the number of lines. For example, setting `line-clamp: 3` will truncate text after the third line.

### Multi-column text

To build multi-column text we use the `column-*` properties.

- `column-count` determines how many columns there should be. It takes an integer as value.
- `column-gap` controls the gap between the columns. It takes a measurement as value.
- `column-rule` is used to add a line between the columns. It takes a measurement, a style, and a color as value (just like a border).

``` css
p {
  width: 50ch;
  column-count: 2;
  column-gap: 2rem;
  column-rule: 3px solid #999;
}
```

### Text direction

The `direction` property of the `<p>` element allows us to control the direction of text. By default it's set to `ltr` (left to right), but we can change it to `rtl` (right to left) when working with right-to-left languages like Hebrew, Farsi, Arabic, etc. Because of this, we usually apply this rule to the `<body>` element.

```css
body {
  direction: rtl
}
```
