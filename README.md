# sass

- [Introduction](#Introduction)
- [Why to Use SASS](#why-to-use-sass)
- [SASS Variables](#sass-variables)
  - [SASS Variable Scope](#sass-variable-scope)
- [SASS Comments](#sass-comments)
  - [Multiline Comments](#multiline-comments)
  - [Single line Comments](#single-line-comments)
- [SASS Nesting](#sass-nesting)
- [SASS Import](#sass-import)
  - [Partial](#partial)

## Introduction

SASS stand for (Syntactically Awesome Stylesheet) is a CSS per-processor,
which helps to reduce repetition in CSS.

It was initially designed by **Hampton Catlin** and developed by **Natalie
Weizenbaum** in 2006. Later, Weizenbaum and Chris Eppstein
used its initial version to extend the Sass with SassScript.

## Why to Use SASS

- It is pre processor language which provide indented syntax for CSS.
- It provides some features that allows to writing code more efficient
  and reusable manners.
- It is a super set of CSS, means its contains all the features for CSS
  and it is open source.
- It allows writing CSS in programming construct.

**_A browser does not support SASS code. Therefore we need SASS pre-processor
to convert SASS into standard CSS_**

SASS file has a extension **.sass**

```sass
$primaryColr: '#365985';
$secondayColr: '#741258';

/* use these variables */
.header {
    background-color: $primaryColr;
}
.footer {
    background-color: $secondayColr;
}
```

## SASS Variables

variables are a way to store information that we can reuse. In sass we can use
these types of variables.

- String
- Numbers
- Colors
- Booleans
- List
- Nulls

**_SASS uses $ symbol to declared a variable_**

```sass
$myFont: Helvetica, sans-serif;
$containerWidth: 300px;
$themeColor: red;
$bodyFontSize: 12px;

body {
  font-family: $myFont;
  font-size: $bodyFontSize;
}
```

### SASS Variable Scope

SASS variable only available where they are defined, scope of sass variables
scope can be override by using **!global**
For example

```sass
$themeColor: red
header {
    $themeColor: green !gloabl
    color: $themeColor
}
footer {
    color: $themeColor
}
```

**CSS Output**

```css
header {
  color: green;
}
footer {
  color: green;
}
```

**Global variables should be defined outside any rules, it should be good
practice to defined all global variables in saperate file like \_global.scss and
inclued the file with @include keyword**

## SASS Comments

Comments are non executable statments which we used in our code, Comments
make source code easier to understand, SASS support two types of comments

- Multiline Comments
- Single line Comments

#### Multiline Comments

These comments written using /\*\*/

#### Single line Comments

These comments are written using //

```sass
/* These are multiline comments example */
// These are single line comments
```

## SASS Nesting

SASS allows us to nest styles as we can do in CSS, Look at an example

```sass
nav{
  ul {
    list-style: none
  }
  li {
    display: inline-block
  }
  a {
    display: block
    text-decoration: none
  }
}
```

## SASS Import

SASS keeps the CSS code DRY (Don't repeat yourself) like in css we can import others files and partial in SASS.
**We can use @import in the following ways**

- As a file extension .css
- http url
- Filename is URL
- @import consist any media queries

```sass
@import "reset.css"
@import "https://khalilahmad.com/testing"
@import url(style)
@import "style" screen
```

### Partial

Partials are SASS or SCSS files, which are written using underscore at the begining of the name.
The partial file name can be imported in SCSS file without using the underscore.
SASS does not compile the CSS file.

**By using underscore it make SASS understand that it is a partial and should not be generate the CSS file.**
