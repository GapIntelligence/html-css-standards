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

## Overview

## HTML Best Practices

## HTML Formatting

## CSS Best Practices

## CSS Formatting
### Name Delimiters
#### Class Names
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
#### States
Use the class prefix `.is-` as in `.is-active` `.is-hidden` `.is-open`. To style, tie it to a class using a Sass `&`
```
.selector {
  &.is-open {
    display: block;
  }
}
```
### Brackets
Place the opening curly-bracket of each rule block on the same line as the last selector. Place the closing curly-bracket of each rule block on its own line after the final property of the rule block. End each property with a semicolon.
```
.selector {
  height: 100vh;
  padding: 1em;
}
```

## Sass

## Accessibility

## Browser and Device Support

