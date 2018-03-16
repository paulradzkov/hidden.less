# hidden.less — responsive visibility classnames

[![npm version](https://badge.fury.io/js/hidden.less.svg)](http://badge.fury.io/js/hidden.less)
[![bower version](https://badge.fury.io/bo/hidden.less.svg)](http://badge.fury.io/bo/hidden.less)

Responsive classnames generator for hidding some HTML depending on media breakpoints.

## Installation

**Compiled from CDN**
[`https://unpkg.com/hidden.less@0.0.2/hidden.css`](https://unpkg.com/hidden.less@0.0.2/hidden.css)
[`https://unpkg.com/hidden.less@0.0.2/hidden.min.css`](https://unpkg.com/hidden.less@0.0.2/hidden.min.css)
[`https://unpkg.com/hidden.less@0.0.2/hidden.min.css.map`](https://unpkg.com/hidden.less@0.0.2/hidden.min.css.map)

**NPM**
`npm install hidden.less --save-dev`

**Bower**
`bower install hidden.less --save`

## How it works

### `.hidden:from-*`

Hides content from selected breakpoint and on larger screens. Example as rendered in CSS:

```css
@media (min-width: 576px) {
  .hidden\:from-sm {
    display: none;
  }
}
```

|                   | **xs**  | **sm**    | **md**    | **lg**     | **xl**   |
| ----------------- | ------- | --------- | --------- | ---------- | -------- |
|                   | 0—575px | 576—767px | 768—991px | 992—1199px | 1200—∞px |
| `.hidden`         | hidden  | hidden    | hidden    | hidden     | hidden   |
| `.hidden:from-xs` | hidden  | hidden    | hidden    | hidden     | hidden   |
| `.hidden:from-sm` |         | hidden    | hidden    | hidden     | hidden   |
| `.hidden:from-md` |         |           | hidden    | hidden     | hidden   |
| `.hidden:from-lg` |         |           |           | hidden     | hidden   |
| `.hidden:from-xl` |         |           |           |            | hidden   |

### `.hidden:upto-*`

Hides content from smaller screens and up to selected breakpoint. Example as rendered in CSS:

```css
@media (max-width: 767px) {
  .hidden\:upto-md {
    display: none;
  }
}
```

|                   | **xs**  | **sm**    | **md**    | **lg**     | **xl**   |
| ----------------- | ------- | --------- | --------- | ---------- | -------- |
|                   | 0—575px | 576—767px | 768—991px | 992—1199px | 1200—∞px |
| `.hidden:upto-sm` | hidden  |           |           |            |          |
| `.hidden:upto-md` | hidden  | hidden    |           |            |          |
| `.hidden:upto-lg` | hidden  | hidden    | hidden    |            |          |
| `.hidden:upto-xl` | hidden  | hidden    | hidden    | hidden     |          |

### `.hidden:between-*-*`

Hides content from one breakpoint to another.

```css
@media (min-width: 576px) and (max-width: 767px) {
  .hidden\:between-sm-md {
    display: none;
  }
}
```

|                         | **xs**  | **sm**    | **md**    | **lg**     | **xl**   |
| ----------------------- | ------- | --------- | --------- | ---------- | -------- |
|                         | 0—575px | 576—767px | 768—991px | 992—1199px | 1200—∞px |
| `.hidden:between-xs-sm` | hidden  |           |           |            |          |
| `.hidden:between-sm-md` |         | hidden    |           |            |          |
| `.hidden:between-md-lg` |         |           | hidden    |            |          |
| `.hidden:between-lg-xl` |         |           |           | hidden     |          |

### `.hidden:print`

For hidding something on print. Doesn't have any breakpoints.

```css
@media print {
  .hidden\:print {
    display: none;
  }
}
```

## Usage in HTML

Link compiled `hidden.css` and apply classes to any HTML element to make them `display:none`.

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

In that example was redefined breakpoints and suffix names.
