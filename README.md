
## Table of contents

- [Overview](#overview)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

This project is a responsive recipe page built based on a Figma design. The main focus was on semantic HTML, clean CSS structure and responsiveness for desktop, tablet and mobile.

### Screenshot

![](./preview.jpg)

### Links

- Solution URL: [https://github.com/keerthana769/Recipe-Page/]
- Live Site URL: [https://keerthana769.github.io/Recipe-Page/]

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties( CSS variables for colors and typography)
- Flexbox
- Desktop-first workflow
- Figma (design reference)


### What I learned

1. **CSS font shorthand**
  ```css
  :root{
  --text-4-ot-bold: 700 16px/150% "Outfit", sans-serif;
  font: <font-style> <font-weight> <font-size>/<line-height> <letter-spacing> <font-family>;
  }
  ```
  The font shorthand resets other font properties. If you need bold text, the font-weight must be included.
  Fonts and required weights must be imported before using them in CSS variables.

2. **Targeting the last table row**
  ```css
  tr:not(:last-child) {
    border-bottom: 1px solid var(--clr-stone-150);
  }
  ```
  td:not(:last-child) checks cells within a row, not rows in a table. `<td>` has no concept of table order. 
  Only `<tr>` understands row order.

3. **Semantic HTML rule of thumb**

  If content has meaning → use a semantic element. If it’s purely for layout → use `<div>` or `<span>`.

4. **Debugging Tip**
  ```css
  * {
    outline: 1px solid red;
  }
  ```
  Helpful for visualizing spacing, overflow, and element boundaries.

5. **width and max-width are used together**
  ```css
  .container {
    width: 100%;
    max-width: 736px;
  }
  ```
  Large screens → width is capped at 736px. Small screens → container shrinks naturally.
  width: 100% allows shrinking on small screens. Ensures responsiveness without media queries.

6. **Adding spacing between list items**
  ```css
  ul {
    list-style-position: outside;
  }
  ```
  global reset removes the default UL indentation completely, we need to add it back manually.
  outside is default browser-style indentation.
  inside → bullets move inside the content area (aligned with text).

7. **Adding spacing between list items**
  ```css
  li:not(:last-child) {
    margin-bottom: 8px;
  }
  ```
  `<ul>` is just a container — it does not represent individual rows/items. So we need to use `<li>`. CSS does not work like table cells here.

8. **How bullet color works**
  ```css
  li {
    color: red;
  }

  ul li::marker {
    color: var(--clr-rose-800);
    font-size: 1.2rem;
  }
  ```
  Bullets inherit their color from the `<li>`, not from the `<ul>`.

  ::marker allows styling list bullets directly. Only color and font-* properties are supported.
  Properties like margin and padding do not work for ::marker.

9. **Using negative margins to offset container padding**
  ```css
  figure {
    margin: 0 -40px;
  }
  ```
  Negative horizontal margins cancel out container padding. Useful when an image needs to visually extend edge-to-edge.

10. **Making images responsive**
  ```css
  img {
    width: 100%;
    height: auto;
  }
  ```
  width: 100% scales the image relative to its container, not the screen.
  height: auto preserves the aspect ratio and prevents image stretching vertically.

11. **Adding borders between table rows**
  ```css
  tr:not(:last-child) {
    border-bottom: 1px solid var(--clr-stone-150);
  }
  ```
  Adds dividers between rows while excluding the last row.

12. **Applying spacing inside table rows**
  ```css
  tr:not(:first-child) td,
  tr:not(:first-child) th {
    padding-top: 12px;
  }
  ```
  `<tr>` elements do not support padding or margin. Spacing must be applied to `<td>` and `<th>` instead.

### Continued development

In the future, this project will be expanded into a small recipe app.
Planned improvements include:
- A home page displaying multiple recipe cards
- Individual recipe pages
- Favorite recipes feature
- Navigation and back button
- Additional recipes and layout refinements

### Useful resources

- [Resource 1](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/border-collapse/) - Used to style and control table borders according to the Figma design.
- [Resource 2](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/border-spacing) - Not used in this project, but useful for handling spacing between table cells.
- [Resource 3](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/box-sizing) - Helped simplify layout calculations when working with padding and margins.
## Author

- Frontend Mentor - [@keerthana769](https://www.frontendmentor.io/profile/keerthana769)
- LinkedIn - [@keerthana-gurram](https://www.linkedin.com/in/keerthana-gurram/)
