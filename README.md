# hidden.less — responsive visibility classnames

[![npm version](https://badge.fury.io/js/hidden.less.svg)](http://badge.fury.io/js/hidden.less)
[![bower version](https://badge.fury.io/bo/hidden.less.svg)](http://badge.fury.io/bo/hidden.less)

Responsive classname generator for hidding some HTML depending on media breakpoints.

## Installation

**Compiled from CDN**  
[`https://unpkg.com/hidden.less@0.0.1/hidden.css`](https://unpkg.com/space.hidden@0.0.1/hidden.css)  
[`https://unpkg.com/hidden.less@0.0.1/hidden.min.css`](https://unpkg.com/space.hidden@0.0.1/hidden.min.css)  
[`https://unpkg.com/hidden.less@0.0.1/hidden.min.css.map`](https://unpkg.com/space.hidden@0.0.1/hidden.min.css.map)

**NPM**  
`npm install hidden.less --save-dev`

**Bower**  
`bower install hidden.less --save`

## How it works



## Usage in HTML

Link compiled `hidden.css` in the head of your page.
Apply classes to any HTML element to make them `display:none`.

## Usage in LESS

Install library with `npm install hidden.less --save-dev` and include its main file inside your project less file:

```less
@import (less) "./node_modules/hidden.less/hidden.less";
```

That is enough to run library with default parameters.

### Default parameters

Parameters stored in mixin:

```less
.hidden-settings() {
    // media breakpoints
    @breakpoints:
        576px,
        768px,
        992px,
        1200px;

    // names for breakpoint suffixes
    @suffixes: xs, sm, md, lg, xl;

    // IMPORTANT: suffixes count should be bigger than breakpoints count by 1
    // suffixes-count = breakpoints-count + 1
}
```

### Redefining parameters

To change any (or every) parameter add setting mixin after import inside your .less file:

```less
@import (less) "./node_modules/hidden.less/hidden.less";

.hidden-settings() {
    // media breakpoints
    @breakpoints:
        768px,
        1024px,
        1440px;

    // names for breakpoint suffixes
    @suffixes: small, medium, large, huge;

    // IMPORTANT: suffixes count should be bigger than breakpoints count by 1
    // suffixes-count = breakpoints-count + 1
}
```

In that example was redefined breakpoints suffix names.
