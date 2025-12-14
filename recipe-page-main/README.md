
## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

### Screenshot

![](./screenshot.jpg)

### Links

- Solution URL: [Add solution URL here](https://your-solution-url.com)
- Live Site URL: [Add live site URL here](https://your-live-site-url.com)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Mobile-first workflow
- [React](https://reactjs.org/) - JS library
- [Next.js](https://nextjs.org/) - React framework
- [Styled Components](https://styled-components.com/) - For styles


### What I learned



```html
<h1>Some HTML code I'm proud of</h1>
```
```css
.proud-of-this-css {
  color: papayawhip;
}
```
```js
const proudOfThisFunc = () => {
  console.log('🎉')
}
```

### Continued development

Use this section to outline areas that you want to continue focusing on in future projects. These could be concepts you're still not completely comfortable with or techniques you found useful that you want to refine and perfect.

### Useful resources

- [Resource 1](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/border-collapse/) - This helped me for XYZ reason. I really liked this pattern and will use it going forward.
- [Resource 2](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/border-spacing) - Used-------------- This is an amazing article which helped me finally understand XYZ. I'd recommend it to anyone still learning this concept.
- [Resource 3](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/box-sizing) - This helped me for XYZ reason. I really liked this pattern and will use it going forward. learned about box sizing

## Author

- Frontend Mentor - [@keerthana769](https://www.frontendmentor.io/profile/keerthana769)
- LinkedIn - [@keerthana-gurram](https://www.linkedin.com/in/keerthana-gurram/)





* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}




2. Styles defined on root (:root)

This is where you put CSS variables or global values like colors and spacing.

:root {
  --clr-primary: hsl(200, 70%, 50%);
  --clr-text: hsl(0, 0%, 20%);
  --space-s: 0.5rem;
  --space-m: 1rem;
}


Now you can use them anywhere:

button {
  background: var(--clr-primary);
  margin-bottom: var(--space-m);
}





B. Use prefixes (common practice)

This makes your variables easy to understand.

Type	Common prefix	Example
Colors	--clr-	--clr-accent, --clr-text
Spacing	--space-	--space-s, --space-l
Font sizes	--fs-	--fs-body, --fs-heading
Font weights	--fw-	--fw-bold
Radii	--radius-	--radius-lg

3. Use lowercase + hyphens
--clr-primary
--clr-neutral-100
4. Try to name variables by purpose, not value

Use purpose-based names:

--clr-primary
--clr-danger
--clr-success


:root is a special selector equal to the <html> element.

You cannot rename it.

But you can define variables inside any selector:

.section-hero {
  --section-color: red;
}


These variables apply only to elements inside .section-hero.



:root {
  --heading-large: 28px/100% 0px "Young Serif", serif;
}
.title {
  font: var(--heading-large);
}




Why this format works

The font shorthand in CSS normally looks like this:

font: <font-size>/<line-height> <font-family>;


But it can also include additional optional values:

font: <font-style> <font-weight> <font-size>/<line-height> <letter-spacing> <font-family>;


You are using this pattern:

font-size / line-height letter-spacing font-family



Important Note

The font shorthand resets many other font-related properties (like weight, style).
So if you need bold, you must include it:

--heading-large-bold: bold 28px/100% 0px "Young Serif", serif;


you must import the font (Young Serif) before using it in your CSS variable.


Correct — you do NOT need that .young-serif-regular class if you are already handling the font through your variable like this:

--heading-large: 28px/100% 0px "Young Serif", serif;



If you're using the font: shorthand → YES

You must specify the weight explicitly in the variable.

Example:

--outfit-regular: 400 16px/140% 0px "Outfit", sans-serif;


Because the font: shorthand resets font-weight unless you include it.



there will be indentation for ul, li but 
Many people use a global reset like:

* {
  margin: 0;
  padding: 0;
}


And this removes the default UL indentation completely, forcing you to add it back manually.



✅ 2. Is there a special CSS property specifically for indentation?

Yes:

list-style-position

outside → bullets stay outside the content box (default)

inside → bullets move inside the content area (aligned with text)

Example:

ul {
  list-style-position: outside; /* default browser-style indentation */
}


But this does not control the exact indentation amount — only how bullets behave.



use padding for indentation of li
ul {
  padding-left: 40px;
}



✅ What this rule does:
ul li:not(:last-child) {
  margin-bottom: 8px;
}

✔ It adds 8px only to li elements that are NOT the last one.
✔ The last <li> gets 0px (because it's excluded).



1. PADDING = Space inside the element

Padding adds space between the element’s border and its content.

Use padding when:
✔ You want the element itself to look bigger
✔ You want more breathing room inside a box
✔ You want to increase clickable/touch area
✔ You’re styling buttons, cards, containers, input boxes, sections

2. MARGIN = Space outside the element

Margin adds space between two separate elements.

Use margin when:
✔ You want space between items (e.g., between two <li>s)
✔ You want to separate sections
✔ You want vertical spacing in your layout
✔ You want to push elements away from each other

Summary Table
Want to do	Use
Add space inside an element	Padding
Add space between elements	Margin
Make boxes bigger (visually)	Padding
Separate 2 components	Margin
Add breathing room inside a card/section	Padding
Indent list items	Padding (UL) or Margin (LI)
Space between list items	Margin


Why this works:
Bullets inherit the color of the list item, not the UL.

So:

ul {
  color: red; /* does NOT color bullets */
}
li {
  color: red; /* DOES color bullets */
}



2. Style bullets with a pseudo-element (FULL CONTROL)
If you want custom colors, spacing, bullet shape, size → use ::marker.

ul li::marker {
  color: var(--clr-rose-800);
  font-size: 1.2rem;
}


To adjust spacing
Move whole list → ul { padding-left }

Space between items → li { margin-bottom }

Space between bullet and text → li::marker { margin-right }



B) text-indent
Moves ONLY the text:

ul li {
  text-indent: 4px;
}



Browser support: ::marker supports color and font-* properties reliably; other properties (margin/padding) are unreliable.


The border-collapse CSS property sets whether cells inside a <table> have shared or separate borders.

When cells are collapsed, the border-style value of inset behaves like ridge, and outset behaves like groove.

When cells are separated, the distance between cells is defined by the border-spacing property.



⭐ You cannot reliably use td:not(:last-child) or th:not(:last-child) to detect the last row.

Why?

Because **:last-child on <td> checks the last cell in the row, not the last row in the table.
This is the key point.

Let me show you clearly.

✅ 1. td:last-child means: “the last cell in THIS row”

Example:

<tr>
  <td>A</td>
  <td>B</td>
</tr>


Here:

td:last-child = <td>B>

NOT the last row of the table

NOT what we need

Doesn't tell you anything about spacing between rows

So:

td:not(:last-child) { ... }


✔ controls spacing between columns
❌ does NOT help with spacing between rows

❌ 2. td cannot tell if it belongs to the last row

Look at this:

<tr class="tr-nutri">
  <td>Calories</td>
  <td>277kcal</td>
</tr>
<tr class="tr-nutri">
  <td>Carbs</td>
  <td>0g</td>
</tr>


If you write:

td:not(:last-child) {
  padding-bottom: 12px;
}


What happens?

It applies padding to the first cell in every row, because that cell is NOT the last cell of its row.

It NEVER knows if it’s in the last row of the table, because a <td> has no concept of table order.

⭐ 3. Only <tr> knows row order

<tr> is the row element.
So only <tr> can answer:

“Am I the last row in this table?”

That’s why this works:

tr:not(:last-child) {
  /* styles for all rows except the last row */
}


But this does NOT work:

td:not(:last-child)


Because that only looks at cells in the same row, not the row in the table.




A global rule (or reset) like img { max-width:100% } or display: inline could be interfering.




Quick facts

max-width limits the element’s width — it will never grow bigger than that, but it may be smaller depending on its natural size or parent.

If the image's intrinsic width is smaller than 656px, max-width:656px will not enlarge it.

If there's another rule (inline style, more specific CSS, or later rule) setting width, that can override or change behaviour.

For responsive images you normally combine width:100% with max-width:656px.


Rule of thumb

Ask yourself:

“Does this content have meaning?”

If yes → use a semantic tag
If no → use <div> or <span>






🧱 Page structure / layout

Use these to define the overall structure of a page.

<header> – Intro section of a page or section

<nav> – Navigation links

<main> – Main content of the page (only one per page)

<section> – A thematic group of content

<article> – Stand-alone, reusable content

<aside> – Side content (related info, notes)

<footer> – Footer of a page or section

🧾 Text content

Use these for readable content.

<h1> to <h6> – Headings (hierarchy matters)

<p> – Paragraph

<blockquote> – Long quotations

<q> – Inline quote

<pre> – Preformatted text

<address> – Contact / author info

<hr> – Thematic break (section divider)

📋 Lists

Use when content is a list.

<ul> – Unordered list

<ol> – Ordered list

<li> – List item

<dl> – Description list

<dt> – Term

<dd> – Description

🖼️ Media & figures

Use for images and media with meaning.

<img> – Image (always include alt)

<figure> – Self-contained media

<figcaption> – Caption for a figure

<audio> – Audio content

<video> – Video content

<track> – Subtitles/captions

🧮 Tables

Use for tabular data only.

<table> – Table container

<caption> – Table title

<thead> – Header rows

<tbody> – Body rows

<tfoot> – Footer rows

<tr> – Table row

<th> – Header cell

<td> – Data cell

🧠 Forms

Use for user input.

<form> – Form container

<label> – Input label

<input> – Input field

<textarea> – Multi-line input

<select> – Dropdown

<option> – Dropdown item

<fieldset> – Group form elements

<legend> – Title for fieldset

<button> – Button

🔗 Interactive & inline semantics

Use for meaning inside text.

<a> – Link

<strong> – Strong importance

<em> – Emphasis

<mark> – Highlighted text

<time> – Date/time

<abbr> – Abbreviation

<code> – Code snippet

<kbd> – Keyboard input

<samp> – Sample output

<cite> – Work title reference

❌ Non-semantic (avoid when possible)

Use only when no semantic tag fits.

<div>

<span>




    *{
            outline: 1px solid red;

    }

  to check for outlines of all the elements for knowing correct spaing, size...best for knowing outlines of contents



  When SHOULD you use border-box?
✅ Use it:

For almost every modern project

When matching Figma designs

When using padding + widths together

For responsive layouts

❌ Rarely use content-box:

Only for very specific low-level cases

Almost never in layout work

That’s why frameworks like:

Bootstrap

Tailwind

Normalize.css

all set box-sizing: border-box globally.



Visual mental model (remember this)
❌ content-box (default)

“Width + padding = bigger box”

✅ border-box

“Width includes padding”





The line in question
figure {
  margin: 0 -40px; /* cancels container padding */
}

1️⃣ What this syntax means
margin: top/bottom  left/right;




1️⃣ What width: 100% means for an image
img {
  width: 100%;
}


This means:

Make the image as wide as its parent container’s content box.




✅ Works perfectly with max-width
.container {
  max-width: 736px;
}
img {
  width: 100%;
}


This is the recommended pattern.


It does NOT stretch image beyond its natural size

If the image file is smaller than the container:

img {
  width: 100%;
}


The browser will stretch it, but:

It may look blurry

Quality may degrade


❌ It does NOT affect height automatically

Height is calculated from the image’s aspect ratio.

Unless you do something wrong like:

img {
  height: 100%;
}


⚠️ That will distort the image.



4️⃣ Why height: auto is often used with it
img {
  width: 100%;
  height: auto;
}


This guarantees:

Aspect ratio is preserved

No image stretching vertically



6️⃣ When NOT to use width: 100%
❌ Don’t use it if:

Image should be smaller than its container

You want fixed-size icons

Image is inline with text

Example:

.icon {
  width: 24px;
}



8️⃣ Mental model (remember this)

width: 100% makes the image fit its container, not the screen.




3️⃣ Why you need BOTH together (this is the key)
When screen is LARGE (e.g. 1200px)

width: 100% → tries to be 1200px

max-width: 736px → caps it at 736px

👉 Final width = 736px

When screen is SMALL (e.g. 360px)

width: 100% → becomes 360px

max-width is ignored because 360 < 736

👉 Final width = 360px






1️⃣ How the browser actually resolves it

Given:

.container {
  width: 100%;
  max-width: 736px;
}


The browser does this in order:

Calculate width

width: 100% → try to be as wide as the parent

Apply max-width constraint

If calculated width > 736px → cap it at 736px

If calculated width ≤ 736px → leave it as-is

So nothing is “overriding” — it’s just a constraint.