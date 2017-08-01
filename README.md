# Gap Intelligence's front-end coding standards
## Table of Contents
1. [Overview](#overview)
2. [HTML Best Practices](#html-best-practices)
3. [HTML Formatting](#html-formatting)
4. [CSS Best Practices](#css-best-practices)
5. [CSS Formatting](#css-formatting)
6. [Sass](#sass)
7. [Accessibility](#accessibility)
8. [Browser/Platform and Device Support](#browserplatform-and-device-support)

# Overview
## Purpose
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

# HTML Best Practices

# HTML Formatting
## Capitalization
Use only lowercase, unless it's for a string.
```
<img src="herbie.jpg" class="image" alt="Herbie, the gap intelligence mascot.">
```

## Closing Tags
Any element with an opening tag needs a closing tag. 
```
<p>Close this paragraph tag.</p>
```
With HTML5, the trailing slash on self-closing tags is now optional. If you're using HTML5, it's good practice not to use trailing slashes. No need to use code that's not needed.

**No**
```
<img src="herbie.jpg" />
<input type="text" />
<br />
```
**Yes**
```
<img src="herbie.jpg">
<input type="text">
<br>
```

## Indentation
Use 2 spaces for indentation in your editor of choice.

## Quotes
Use double quotes around attribute values.
```
<input type="text" class="search">
```

## Trailing Whitespace
Remove all trailing whitespace.

# CSS Best Practices
## Encoding
Do not include a `@charset` in the CSS.
```
/* DO NOT */
@charset "UTF-8";

.selector {
  color: #fff;
}
```

## Classes and IDs
Do not use `id` for styling purposes

Acceptable uses for `id` include:

- JavaScript selection - prefix these with js- to indicate they are for JavaScript only
- Assigning form labels to inputs
- Jump links between sections of a page

```
<section class="jumbotron" id="js-jumbotron"> ... </section>
```
```
<label for="first-name">First Name</label>
<input id="first-name" type="text" />
```
```
<a href="#about">Skip to About section</a>

...

<section id="about"> ... </section>
```

## Selector Specificity
Keep selector [specificity](https://www.smashingmagazine.com/2007/07/css-specificity-things-you-should-know/) as low as possible, opting for a single class as the best selector.
```
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

# CSS Formatting
## Capitalization
Do not use capitalization, all classes and ids should be lowercase and delimited as [documented below](#name-delimiters).

## Name Delimiters
**Class Names**

Use BEM for class names. Prefix the parent class with `.b-`

```
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
**States**

Use the class prefix `.is-` as in `.is-active` `.is-hidden` `.is-open`. To style, tie it to a class using a Sass `&`
```
.selector {
  &.is-open {
    display: block;
  }
}
```
## Brackets
Place the opening curly-bracket of each rule block on the same line as the last selector. Place the closing curly-bracket of each rule block on its own line after the final property of the rule block. End each property with a semicolon.
```
.selector {
  height: 100vh;
  padding: 1em;
}
```
## Indentation
Use 2 spaces for indenting. Indent each property in a rule block 2 spaces.
```
.selector {
  height: 100vh;
  padding: 1em;
}
```
## Property Whitespace
Put each property on its own line. Follow each property with a colon and a single space.
```
.selector {
  height: 100vh;
  padding: 1em;
}
```
## Semicolons
Follow each property value with a semi-colon.
```
.selector {
  height: 100vh;
  padding: 1em;
}
```
## Trailing Whitespace
Remove all trailing whitespace.

## Rule Block Separation
Separate each rule block with a line break.
```
.selector-one {
  height: 100vh;
  padding: 1em;
}
.selector-two {
  display: flex;
  margin: 1em;
}
```
## Property Order
CSS properties should be grouped alphabetically for easing scanning and locating.
```
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
## Vendor Prefixes
Ain't nobody got time for that. Install the [Autoprefixer gem](https://github.com/ai/autoprefixer-rails) then celebrate with a cocktail. 

## Multi-Value Properties
Format multi-value properties by starting a new line for each value and indenting each line 2 spaces.
```
.selector {
  background: 
    transparent url("gay-bath-house.jpg") 0 0/cover no-repeat;
    transparent url("eugene-correia.png") 50% 25% no-repeat; 
}
```

## Single Properties
It's ok to put rule blocks with a single property on a single line. Include a space after the opening bracket and before the closing bracket.
```
.selector { height: 100vh; }
```

## Multiple Selectors
Separate multiple selectors in the same rule block with a comma and place each selector on a new line.
```
.selector:hover,
.selector:focus {
  color: #555;
}
```

## Comments and Grouping
Group related rule blocks by base object using the standardized section comment style.
```
/* block: nav */
.b-nav {
  background-color: #fff;
  display: flex;
}
```
If a section requires additional subsets of comments, a single line comment is acceptable.

If a property / value pair needs additional clarity or is not self-documenting, add comments on the same line immediately following the value.
```
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

## Hexadecimal Notation
Always use six character and lowercase hexadecimal notation, this includes inside Sass variables. If the hexcode's 6 characters are identical, it's ok to shorthand the hexcode to 3 characters.
```
.selector-one {
  color: #f5f5f5;
}
.selector-two {
 color: #555; /* the same as #555555 */
}
```
## TODO Comments
Mark todos and action items with a comment that includes `TODO`. Be sure that `TODO` is always uppercase.
```
/* TODO - refactor this into a shorthand property */
.selector {
  color: #fff;
  font-family: "lato", Helvetica, sans-serif;
  font-size: 1.2em;
  font-weight: 500;
  line-height: 1.4;
}
```

## Table of Contents
Ain't nobody got time or use for this. Don't bother adding a table of contents in the CSS please.

# Sass

# Accessibility

# Browser/Platform and Device Support
## Browser/Platform
**Mac**
- The latest versions of Chrome, Firefox, and Safari.

**PC**
- The latest versions of Chrome and Firefox
- IE 10 and newer
- Windows 8 and newer

## Device Support
- All mobile, tablet, laptop and desktop devices >= 320px wide.
