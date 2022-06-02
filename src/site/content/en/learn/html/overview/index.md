---
title: HTML Overview
description: >
  Introduction to HTML: elements, attributes, and how HTML interacts with CSS and JavaScript.
authors:
  - estelle
date: 2022-12-31
---

HyperText Markup Language, or HTML, is the standard markup language for describing the structure of documents displayed on the web. HTML consists of a series of elements and attributes which are used to mark up all the components of a document to structure it in a meaningful way.

HTML documents are basically a tree of HTML nodes, including HTML elements and text nodes. HTML elements provide the semantics and formatting for documents, including creating paragraphs, lists and tables, and embedding images and form controls. Each element may have multiple attributes specified. Many elements can have content, including other elements and text. Other elements are empty, with the tag and attributes defining their function.

There are several categories of elements, including metadata, sectioning, text, inline semantic, form, interactive, media, component, and scripting. We’ll cover most of these in the series. But first, what is an element? 

## Elements 

HTML consists of a series of elements, which you use to enclose, or wrap, different parts of the content to make it appear a certain way, or act a certain way. HTML elements are delineated by tags, written using angle brackets. 

Our page title is a heading, level one, for which we use the `<h1>` tag. The actual title, “Machine Learning Workshop” is the content of our element. The content goes between the open and closing tags. The entire thing–the opening tag, closing tag, content, and the content–is the element.


The closing tag is the same tag as the opening tag, but preceded by a slash.

Elements and tags aren’t the exact same thing, though many people use the terms interchangeably. The tag is the content in the brackets. In this case, the `<h1>`. An “element” is the opening and closing tag and all the content between those tags, including nested elements.

```html
<p>This paragraph has some <strong><em>strongly emphasized</em></strong> content</p>
```

This paragraph element has other elements **nested** in it.  When nesting elements, it’s important that they are properly nested.  HTML tags should be closed in the rever​​se order of which they were opened. In the above example, notice how the `<em>` is both opened and closed within the opening and closing `<strong>` tags, and the `<strong>` is both open and closed within the `<p>` tags. 

Browsers do not display the HTML tags. They are used to interpret the content of the page. 

HTML is very, very forgiving. For example, if we omitted a closing </ul> or `</li>` closing tags, the closing tags are implied. 

```html
<ul>
    <li>Blendan Smooth
    <li>Hoover Sukhdeep
    <li>Toasty McToastface
```

While legal to not close an `<li>`, this isn’t good practice.  The closing `</ul>` is mandatory. The browser will try to determine where your list and list items ended, but you might not agree with the decision. 

The specifications list whether the closing tag is mandatory or not. “Neither tag is omissible” in the specification means both an opening tag and a closing tag are required. 

Had the `<em>` or `<strong>` above not been closed, the browser may or may not close the element for you. Not closing an `<em>` simply leads to content possibly being rendered differently than you intended. Not closing some tags, like `<script>`, `<style>`, `<template>`, `<textarea>` and `<title>`, breaks subsequent content. 

Having some content unintendingly being italic won’t destroy your business. Having most of your content appear unstyled in a 200x300 textarea becasue you forgot a `</textarea>` or not show up at all because you forgot to close a `</style>` makes the site unusable.

Sometimes elements are there even if the tags aren’t. Because elements can be implied, an element can exist even when the tags don’t. The browser will add a `<body>` tag even if you don’t. That being said, while it is “legal” to omit tags, don’t. Also, as mentioned above, make sure they are correctly nested. Your future-self as a maintainer of markup will thank you.

The element you choose, and therefore the tags you use, should be appropriate for the content you are displaying as tags have semantic meaning. The [semantics](SECTION LINK), or `role`, of an element is important to assistive technologies and, in some cases, search engines.  

There are two types of elements: replaced and non-replaced. 

### Non replaced element

The paragraph and header above are both non-replaced. Non-replaced elements have tags that surround and provide information about document text and may include other tags as sub-elements. These enclosing tags can make a phrase or image hyperlink to somewhere else, can turn a sentence into a header, can give emphasis to words, and so on. 

### Replaced and void elements

Replaced elements, like `<img>` and `<input>`, are replaced by non-text content; an image and a graphical user interface object for these two elements, respectively.  

```html
<input type=”range”>
<img src="switch.svg" alt="light switch">
```
—
Output of the above HTML:
<input type=”range”>
<img src="https://machinelearningworkshop.com/svg/switch2.svg" alt="light switch" height="100">
—

Replaced elements are all self-closing elements and are represented by one tag. This means there is no such thing as a closing tag for a replaced element. Optionally, you can include a slash at the of the tag, which many people find makes markup easier to read:

```html
<input type=”range”/>
<img src="switch.svg" alt="light switch"/>
```
Replaced elements are all “void elements”, bit not all void elements are replaced. Void elements  can not contain text content or nested elements. Void elements include  `<area>`, `<base>`, `<br>`, `<col>`, `<embed>`, `<hr>`, `<img>`, `<input>`, `<link>`, `<meta>`, `<source>`, `<track>`, and `<wbr>`. The slash at the end is old school: it’s a way of indicating that the element is self-closing and there will be not matched end or closing tag. Why have a void element, which can’t have any content, that isn’t replaced and thereby doesn’t render anything to the screen? To provide information about the content! The information is provided by the elements’ attributes.

## Attributes

You may have noticed the `<img>` and `<input`> examples had more than just the element type in their opening tag. These extra bits of space-separated name/value pairs are called “attributes.” Attributes are what make HTML so incredibly powerful. We’ll be covering hundreds of attribute and attribute values in this series, but here we’ll just discuss what they are in general and how to include them.

Attributes provide information about the element. The attribute, like the rest of the tag, won't appear in the content, but they do help define how the content will appear to both your sighted and non-sighted (assistive technologies and search engines) users. 

Attributes only appear in the opening tag. The opening tag starts with the element type, followed by a space, and then zero or more attributes. When an element has more than one attribute, the attributes should be separated by one or more spaces. The attribute name is followed by an equal sign equating it with the attribute value, wrapped with open and closing quotations marks. 



In this example, we have an anchor link with two attributes . These two attributes have converted the content “Registration” into an internal anchor link.  When it is clicked, tapped, or activated with the keyboard or other device, the element with the attribute `id=”register’` in its opening tag will scroll into view . 

Attributes define the behavior, linkages, and functionality of elements. We’ll cover more attributes in the [Attribute](LINK) section of this series. For right now, just note that some attributes are global - meaning they can appear within any element’s opening tag - some apply only to some elements, and yet others are element specific relevant only to a single element. 

Most attributes are name/value pairs. Boolean attributes, whose value is true, false, or the name of the attribute, can be included as just the attribute: the value is not necessary. 

```html
<img src="switch.svg" alt="light switch" ismap />
```
This image has three attributes: `src`, `alt`, and `ismap`. The `src` attribute is used to provide the URL for the image. The `alt` attribute provides alternative text for the image. The ` ismap` attribute is Boolean, and doesn’t require a value. This is just to explain what attributes are. We’ll cover these attributes in more detail in the [images](IMAGES) section.

While quoting attributes isn’t always required, it sometimes is. If the value has a space or special characters, quotes are needed, so, just in case, quoting is always recommended. One or more spaces aren’t actually required between attributes if the attribute value is quoted, but, to be safe, and for legibility, quotes and spaces are always recommended. 

HTML is not case-sensitive, but some attribute values are. Values that are not defined as keywords are generally case sensitive including `id` and `class` values. 

Note that if an attribute value is case sensitive in HTML, it is case sensitive when used in an [attribute selector](ATTRIBUTE SELECTOR).

To make markup easier to read, it is recommended, but not required, to mark up your HTML using lowercase letters for all your element names and attribute names within your tags, and quote all attribute values.  If you ever hear the term “XHTML style markup”, this, and self closing empty elements with a slash at the end, is what that means. 

## Appearance of Elements

The default appearance of semantic elements is set by user-agent stylesheets. Most browsers use actual stylesheets for this purpose, while others simulate them in code. The end result is the same. Although some constraints on user-agent stylesheets are set by the HTML specification, browsers have a lot of latitude, which means some differences exist between browsers.  

HTML should be used to structure content, not to define content's appearance. The appearance is the realm of CSS. While many elements that alter the appearance of content, such as `<h1>`, `<strong>`, and `<em>`, have a semantic meaning, the appearance can and generally will be changed with author styles. 


<h1>This header has both <strong>strong</strong> and <em>emphasized</em> content</h1>


## Element, Attributes, and JavaScript

The Document Object Model (DOM) is the data representation of the structure and content of an HTML document.  As the browser parses HTML, it creates a JavaScript object for every element and sections of text encountered. These objects are called nodes - element and text nodes, respectively.  The HTML DOM API provides access to and control of every HTML element via the DOM. 

There is an interface to define the functionality of every HTML element.  The [HTML DOM API](https://developer.mozilla.org/docs/Web/API/HTML_DOM_API) provides the `HTMLElement` interface and all the HTML classes that inherit from it, including `HTMLAnchorElement`, HTMLImageElement, etc.  

The `HTMLElement` interface represents the HTML element and all of its descendant nodes. Some elements directly implement the `HTMLElement` interface, while others implement it via an interface that inherits it. Each inheriting interface has a constructor, methods, and properties.  Via the inherited `HTMLElement` properties you can access every global attribute, and input, pointer, transition, and animation events. Via the individual element’s sub-type, such as [`HTMLImageElement`](https://developer.mozilla.org/docs/Web/API/HTMLImageElement), you can access element-specific attribute values and methods.

## Check your understanding


