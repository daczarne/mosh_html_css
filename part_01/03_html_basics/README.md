# HTML

[Head section](#head-section)  
[Text](#text)  
[Entities](#entities)  
[Hyperlinks](#hyperlinks)  
[Images](#images)  
[Video and audio](#video-and-audio)  
[Lists](#lists)  
[Tables](#tables)  
[Containers](#containers)  
[Semantic elements](#semantic-elements)  
[Structuring a web page](#structuring-a-web-page)  

## Head section

We use the head section to give browsers and search engines information about the webpage. We use the self-closing `<meta/>` tag to define metadata about the page. This includes the following:

``` html
<meta charset="UTF-8" />
```

This `meta` defines the character set of the webpage. Nowadays the most commonly used one is `UTF-8`.

Then comes a `meta` for configuring the viewport:

``` html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

The **viewport** is the visible area of a webpage. This area changes depending on the device that the user is using. In the `content` attribute we define the initial width (`width=device-width`), and the zoom factor (`initial-scale=1.0`) of the page.

Another `meta` is the `keywords` meta. This allows us to define keywords for the webpage that are used for search engines for prioritizing results.

``` html
<meta name="keywords" content="HTML, CSS">
```

The `description` meta will be displayed in search results when the page is listed as a query result.

``` html
<meta name="description" content="A description of the page" />
```

## Text

The most common element for working with text is the `<p>` (paragraph) element. To add emphasis to a word or sequence of words we wrap them in the `<em>` element. We can use CSS to define how the `<em>` tag should format our text. An other element for targeting text for special formatting is `<strong>`. By default it will display elements in bold, but this can also be modified with CSS.

There are six levels of heading in HTML, from `<h1>` to `<h6>`. The style of the text can be changed with CSS therefore, h-tags should not be used based on their default style (for example, their size), but rather based on the importance of the heading itself, with `<h1>` representing the most important heading, and going down in importance from there. They should represent hierarchy. As such, every page should have one, and only one, `<h1>` heading (since there can only be one *most important heading*). Headings should appear as needed, but in order. For example, after the `<h1>` we should not jump to `<h4>`, but rather to `<h2>`, and change the style if needed.

## Entities

Some characters are reserved in HTML (as with any other language) and need to be escaped. To do so, we use HTML-entities. All entities start with an ampersand (`&`) and end with a semi-colon (`;`). Each entity is then represented with a character sequence. For example, an less-than sign is `&lt;`, or greater-than sign is `&gt;`.

Other common entities include:

- `&copy;` for the copyright symbol
- `&nbsp;` for the non-breaking space
- `&commat;` for adding an at (`@`)
- `&amp;` for adding an ampersand (`&`)

The complete list can be found [here](https://dev.w3.org/html5/html-author/charref).

## Hyperlinks

> **Hyperlink:** an element the user can interact with (generally, by clicking on it)
> **Link:** the address or URL of a resource

Hyperlinks are created with the anchor tag: `<a>`. The link to which it must point is supplied via the `href` attribute by passing the URL. The URL can be relative or absolute. To go one level up in a relative URL use `../`. Absolute URLs start at the root of the project and need to start with `/`.

Apart from the anchor itself we need to add a text or image that the user can click on. To add and image use the `<img>` tag.

We can link to other resources like images too. If we want to user to download the resource (instead of it being displayed on the page) we use the `download` attribute. This attribute does not have a value.

Hyperlinks can also link to other parts of the page. To do so, we create an anchor who's `href` attribute set to the ID of the element we want to link.

``` html
<a href="#element-id">Display text</a>
```

With this we can also link to the top of the page by using an "empty" `href`:

``` html
<a href="#">Jump to top</a>
```

When linking to external webpages we just need to pass the URL of the page, starting with the protocol (generally, `https://`). When doing so, we generally make the link open in a separate tab or window since we don't want the user to leave our page. To do so we set the `target` attribute to `_blank`.

``` html
<a href="https://google.com" target="_blank">Google</a>
```

Lastly, to link to emails we just need to pass `mailto:email@address.com` to the `href` attribute. When the user clicks on it, his/hers mail client will open with the `to:` field populated to the email address that we specify.

## Images

## Video and audio

## Lists

## Tables

## Containers

## Semantic elements

## Structuring a web page
