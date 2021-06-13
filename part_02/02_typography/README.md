# Typography

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
