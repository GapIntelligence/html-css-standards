# Gap Intelligence's front-end coding standards
## Table of Contents
1. Overview
2. HTML Best Practices
3. HTML Formatting
4. CSS Best Practices
5. CSS Formatting
6. Sass
7. Accessibility
8. Browser and Device Support

# Overview

# HTML Best Practices

# HTML Formatting

# CSS Best Practices

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
- All mobile, tablet, laptop and desktop devices 320px wide and greater.
