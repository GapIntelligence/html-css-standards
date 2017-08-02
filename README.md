# Gap Intelligence's Front-end Coding Standards
## Table of Contents
1. [Overview](#overview)
2. [HTML](#html)
3. [CSS](#css)
4. [Browser/Platform and Device Support](#browserplatform-and-device-support)

# Overview
### PURPOSE
The pupose of this document is to set coding standards so that Gap Intelligence has consistency and cohesion in their front-end code.

Done is better than perfect, and every project is different. That being said, it's not always a necessity to follow these rules exactly. Simply strive for your code to be:
* Semantic
* Reusable
* Scalable
* Flexible
* Maintainable
* Understandable
* Performant
* Optimized
* Accessible

# HTML
### BOOLEAN ATTRIBUTES
Boolean attributes should not have a value.
```html
<input type="text" disabled>
```

### CAPITALIZATION
Use only lowercase, unless it's for a string.
```html
<img src="herbie.jpg" class="image" alt="Herbie, the gap intelligence mascot.">
```

### CLOSING TAGS
Any element with an opening tag needs a closing tag. 
```html
<p>Close this paragraph tag.</p>
```
With HTML5, the trailing slash on self-closing tags is now optional. If you're using HTML5, it's good practice not to use trailing slashes. No need to use code that's not needed.

**No**
```html
<img src="herbie.jpg" />
<input type="text" />
<br />
```
**Yes**
```html
<img src="herbie.jpg">
<input type="text">
<br>
```

### COMMENTS
Use standard HTML comments liberally to add structure and clarity to your code.
```html
<!-- Start of main content -->
<section class="b-main-content">...</section>
<!-- End of main content -->
```

### DOCTYPES
Use the HTML5 doctype.
```html
<!doctype html>
```

**Resources**
* https://www.w3schools.com/tags/tag_doctype.asp

### ENCODING
Use UTF-8 encoding. This meta tag should be the first element inside the document's `<head>` element.
```html
<meta charset="utf-8">
```

### HTML ENTITIES
Use appropriate HTML entity names or numbers for special characters.
```html
&copy; 2017 Gap Intelligence &amp; Herbie the Hedgehog &#8482;
```

**Resources**
* https://www.freeformatter.com/html-entities.html

### HTML TEMPLATING LANGUAGES
Always an HTML templating language like Slim, Haml, or Jade when possible. Ain't nobody got time to write standard HTML. It's time consuming and can be difficult to manage the closing of tags. Slim has been Gap Intelligence's language of choice because it processes slightly faster than it's competition, but if you feel something else works better for you, use it. Just be sure to run it by the backend team as they have to write HTML sometimes as well.

### HTML5 ELEMENTS
Use HTML5 elements where possible. Some such as `<canvas>` and `<video>` has limited browser support at this time. If you use elements with limited support, always be sure to include a fallback. If you're unsure about an elements support, use the resource below.

**Resources**
* http://caniuse.com

### HTML5 FORM VALIDATION
By default, many HTML5 form inputs include validation that is provided by the browser. In many cases the browser implemented messages are not desired and/or your application may have it's own validation and error messaging in place. In order to remove validation (and thereby the default browser messages) use the `novalidate` attribute on the containing form.
```html
<form action="#" method="post" novalidate>
  <label for"email">Email Address:</label>
  <input type="email" placeholder="Enter a valid email address" id="email">
  <button type="submit">Submit</button>
</form>
```

### IMAGE FORMATS
Know the pros/cons of each image format and use whatever best suits your needs. In general at Gap Intelligence we use:
* .jpg
* .png
* .svg
* .gif

**Resources**
* https://en.wikipedia.org/wiki/Image_file_formats

### INDENTATION
Use 2 spaces for indentation in your editor of choice.

### QUOTES
Use double quotes around attribute values.
```html
<input type="text" class="search">
```

### SEMANTIC MARKUP
Write clean, semantic markup that adds structure and clarity to the code. Just as important, it should also reinforce the meaning of the page content.
```html
<main>
  <section class="about">
    <article>
      <h1>About Us</h1>
      <p>We da shit, son.</p>
    </article>
  </section>
</main>
```

**Resources**
* http://www.hongkiat.com/blog/html-5-semantics
* https://css-tricks.com/video-screencasts/100-lets-write-semantic-markup

### TABLES
Tables should only be used for tabular data and never, ever used for page layouts. Below is standard markup for a table. The tags `<thead>` and `<tfoot>` can be omitted if the table doesn't have a header or footer.
```html
<table>
  <thead>
    <tr>
      <th>Merchant</th>
      <th>Product</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Amazon</td>
      <td>15" Macbook Pro</td>
    </tr>
  </tbody>
</table>
```

### TODO COMMENTS
Mark todos and action items with a comment that includes `TODO`. Be sure that `TODO` is always uppercase.
```html
<!-- TODO - refactor later with HTML5 tags -->
<div class="main-content">
  <div class="article">...</div>
</div>
```

### TRAILING WHITESPACE
Remove all trailing whitespace.

### TYPE ATTRIBUTES
**HTML5 Doctype**

When working with HTML5, the `type` attribute is no longer needed for stylesheets and scripts.
```html
<link rel="stylesheet" href="main.css">
<script src="main.js">
```
**Legacy Doctypes**

When working with doctypes older than HTML5, the `type` attribute is required.
```html
<link rel="stylesheet" href="main.css" type="text/css" />
<script src="main.js" type="text/javascript" />
```

### W3C VALIDATION
* Write valid code.
* Remaining errors and warnings should be intentional.

**Resources**
* http://validator.w3.org

# CSS
### BRACKETS
Place the opening curly-bracket of each rule block on the same line as the last selector. Place the closing curly-bracket of each rule block on its own line after the final property of the rule block. End each property with a semicolon.
```css
.selector {
  height: 100vh;
  padding: 1em;
}
```

### BROWSER HACKS
Browser hacks should only be used on browsers <= IE10. Other than our legacy applications (gapTCO, Data Center, etc.), Gap Intelligence only supports browsers >= IE11 on platforms >= Windows 8. This decision was made because as of January 12, 2016, Microsoft stopped supporting IE10 and older. At this point, Chrome, FF, Safari, Edge, and IE11+ are W3C standards compliant on both Mac and PC. This means any browser inconsistencies with your code should be solvable without resorting to browser hacks. Of course nothing is perfect, so if you find yourself in a bind, feel free to use browser hacks, but make it a point to come back later and try to fix it without hacking.

**Resources**
* http://browserhacks.com

With legacy applications, it's preferable to use conditional comments over browser hacks if you have a large amount of code targeted at a specific browser.
```html
<!--[if IE 9]><link href="ie9.css" rel="stylesheet" /><![endif]-->
<!--[if lte IE 8]><link href="ie8.css" rel="stylesheet" /><![endif]-->
<!--[if lte IE 7]><link href="ie7.css" rel="stylesheet" /><![endif]-->
<!--[if lte IE 6]><link href="ie6.css" rel="stylesheet" /><![endif]-->
```

### CAPITALIZATION
Do not use capitalization, all classes and ids should be lowercase and delimited as [documented below](#name-delimiters).

### CLASSES AND IDS
Do not use `id` for styling purposes

Acceptable uses for `id` include:

- JavaScript selection - prefix these with js- to indicate they are for JavaScript only
- Assigning form labels to inputs
- Jump links between sections of a page

```html
<section class="jumbotron" id="js-jumbotron"> ... </section>
```
```html
<label for="first-name">First Name</label>
<input id="first-name" type="text">
```
```html
<a href="#about">Skip to About section</a>

---

<section id="about"> ... </section>
```

### COMMENTS AND GROUPING
Group related rule blocks by base object using the standardized section comment style.
```css
/* block: nav */
.b-nav {
  background-color: #fff;
  display: flex;
}
```
If a section requires additional subsets of comments, a single line comment is acceptable.

If a property / value pair needs additional clarity or is not self-documenting, add comments on the same line immediately following the value.
```css
/* block: b-nav */
.b-nav {
  background-color: #fff;
  display: flex; /* will not work in <IE10 */
}
/* resize the logo for retina screens and adjust it's padding accordingly */ 
.nav__logo {
  background: transparent url("logo.png") 0 0 no-repeat;
  background-size: 50%;
  padding: 0 .5em;
}
```

### ENCODING
Do not include a `@charset` in the CSS.
```css
/* DO NOT */
@charset "UTF-8";

.selector {
  color: #fff;
}
```

### HEXADECIMAL NOTATION
Always use six character and lowercase hexadecimal notation, this includes inside Sass variables. If the hexcode's 6 characters are identical, it's ok to shorthand the hexcode to 3 characters.
```css
.selector-one {
  color: #f5f5f5;
}
.selector-two {
 color: #555; /* the same as #555555 */
}
```

### INDENTATION
Use 2 spaces for indenting. Do it.
```css
.selector {
  height: 100vh;
  padding: 1em;
}
```

### MULTI-VALUE PROPERTIES
Format multi-value properties by starting a new line for each value and indenting each line 2 spaces.
```sass
.selector {
  background: 
    transparent url("main-background.jpg") 0 0/cover no-repeat;
    transparent url("overlay-background.png") 50% 25% no-repeat; 
}
```

### MULTIPLE SELECTORS
Separate multiple selectors in the same rule block with a comma and place each selector on a new line.
```css
.selector:hover,
.selector:focus {
  color: #555;
}
```

### NAME DELIMITERS
**Class Names**

Use BEM for class names. Prefix the parent class with `.b-`

```css
.block {
  padding: 0;
}
.block__element {
  padding: 0;
}
.block__element--modifier {
  padding: 0;
}
```

**Resources**
* https://css-tricks.com/bem-101
* https://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax
* https://www.sitepoint.com/bem-smacss-advice-from-developers

**States**

Use the class prefix `.is-` as in `.is-active` `.is-hidden` `.is-open`. To style, tie it to a class using a Sass `&`
```sass
.selector {
  &.is-open {
    display: block;
  }
}
```

### PROPERTY ORDER
CSS properties should be grouped alphabetically for easing scanning and locating.
```css
.selector {
  align-items: center;
  background-color: #eee;
  display: flex;
  flex-flow: column wrap;
  height: 100vh;
  margin: 0 1em;
  opacity: 1;
  overflow: hidden;
  padding: 1em;
  visibility: visible;
  transition: all .2s;
}
```

### PROPERTY WHITESPACE
Put each property on its own line. Follow each property with a colon and a single space.
```css
.selector {
  height: 100vh;
  padding: 1em;
}
```

### RULE BLOCK SEPARATION
Separate each rule block with a line break.
```css
.selector-one {
  height: 100vh;
  padding: 1em;
}
.selector-two {
  display: flex;
  margin: 1em;
}
```

### SELECTOR SPECIFICITY
Keep selector [specificity](https://www.smashingmagazine.com/2007/07/css-specificity-things-you-should-know/) as low as possible, opting for a single class as the best selector.
```sass
/* Do this */
.article__header--large {
  font-size: 4em;
  line-height: 1.6;
}

/* Don't do this shit */
.article {
  .header {
    .large {
      font-size: 4em;
      line-height: 1.6;
    }
  }
}

/* Don't overquality selectors if not needed, it increases specificity. in the example below, the ul is not needed. */
ul.list {
  list-style: none;
}
```

### SEMICOLONS
Follow each property value with a semicolon.
```css
.selector {
  height: 100vh;
  padding: 1em;
}
```

### SHORTHAND
Use shorthand where possible unless setting a single value. Check out the handy reference guide with all the CSS properties that utilize shorthand below. 

**Resources**
* https://www.w3.org/community/webed/wiki/CSS_shorthand_reference

### SINGLE PROPERTIES
It's ok to put rule blocks with a single property on a single line. Include a space after the opening bracket and before the closing bracket.
```css
.selector { height: 100vh; }
```

### TABLE OF CONTENTS
Ain't nobody got time or use for this. Don't bother adding a table of contents in the CSS please.

### TODO COMMENTS
Mark todos and action items with a comment that includes `TODO`. Be sure that `TODO` is always uppercase.
```css
/* TODO - refactor this into a shorthand property */
.selector {
  color: #fff;
  font-family: "lato", Helvetica, sans-serif;
  font-size: 1.2em;
  font-weight: 500;
  line-height: 1.4;
}
```

### TRAILING WHITESPACE
Remove all trailing whitespace.

### VENDOR PREFIXES
Ain't nobody got time for that. Install the [Autoprefixer gem](https://github.com/ai/autoprefixer-rails) then celebrate with a cocktail. 

### W3C VALIDATION
* Write valid code.
* Remaining errors and warnings should be intentional.

**Resources**
* http://jigsaw.w3.org/css-validator
* http://csslint.net

# Browser/Platform and Device Support
### BROWSER/PLATFORM
**Mac**
- The latest versions of Chrome, Firefox, and Safari.

**PC**
- The latest versions of Chrome and Firefox
- IE 10 and newer
- Windows 8 and newer

### DEVICE SUPPORT
- All mobile, tablet, laptop and desktop devices >= 320px wide.
