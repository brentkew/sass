# sass

- [Introduction](#introduction)
- [Why to Use SASS](#why-to-use-sass)
- [SASS Variables](#sass-variables)
  - [SASS Variable Scope](#sass-variable-scope)
- [SASS Comments](#sass-comments)
  - [Multiline Comments](#multiline-comments)
  - [Single line Comments](#single-line-comments)
- [SASS Nesting](#sass-nesting)
- [SASS Import](#sass-import)
  - [Partial](#partial)
- [Directives and Expressions](#directives-and-expressions)
  - [Some Directives and Expressions](#some-directives-and-expressions)
- [Mixin](#mixin)
  - [Using of Mixin](#using-of-mixin)
  - [Default Value of Mixin](#default-value-of-mixin)
- [Extend Directive](#extend-directive)

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
$primaryColr: '#365985'
$secondayColr: '#741258'

/* use these variables */
.header {
    background-color: $primaryColr
}
.footer {
    background-color: $secondayColr
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
$myFont: Helvetica, sans-serif
$containerWidth: 300px
$themeColor: red
$bodyFontSize: 12px

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
  &:hover {
      text-decoration: underline;
  }
  &::after {
      content: "Hello"
  }
}

these nesting code equals to below mentioned CSS
nav ul{}
nav li{}
nav a{}
nav a:hover{}
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

## Directives and Expressions

Styling based on some conditions or applying same style many times can be accomplished by using control directives and expressions.

## Some Directives and Expressions

- if()
- @if / @else
- @for
- @each
- @while

### if()

This built in if() function returns only one result from two possible outcomes.

```php
if(express, value1, value2)
```

```scss
$value1: 2;
$value2: 2;
.heading h2 {
  color: if($value1 + $value2 == 2; green, red);
}
```

### @if()

@if directive accepts SASS script expression and uses nested styles whenever the result is anything otherthen **false** and **null**

```scss
$value1: 1;
$value2: 2;
.atIfDirective {
  p {
    @if $variable1 + $variable2 == 2 {
      border: 5px solid #c3c3c3;
      font-size: 30px;
    }
  }
}
```

@if directive also used as if else statment

```scss
@if expression {
  // CSS codes
} @else if condition {
  // CSS codes
} @else {
  // CSS codes
}

$authorType: "admin";
.ifElseDirective {
  p {
    font-size: 32px;
    @if $authorType == "editor" {
      color: green;
    } @else if $authorType == "admin" {
      color: blue;
    } @else {
      color: red;
    }
  }
}
```

### @for

The @for directive allows you to generate styles in a loop. The counter variable is used to set the output for each iteration.

### @while

The @while directive also takes SassScript expressions and until the statement evaluates to false, it iteratively outputs nested styles.

```scss
$i: 5;
@while $i > 0 {
  .paddding-#{$i} {
    padding-left: 1px * $i;
  }
  $i: $i - 10;
}
```

## Mixin

Mixin allows us to create a group of styles, which are reusable throughout your stylesheet.
It helps us to avoid writing repetitive codes.
Mixin can be defined like this
@mixin

Following are the steps to use a mixin

- Defining a Mixin
- Including a Mixin
- Arguments

```scss
@mixin boldText {
  color: green;
  font-size: 32;
  font-weight: bold;
  border: 1px solid #c3c3c3;
}
```

### Using of Mixin

```scss
@mixin notification {
  color: green;
  font-size: 32px;
  font-weight: bold;
}
.success {
  @include notification;
}
.danger {
  @include notification;
}
```

**_Mixin with Arguments_**

```scss
@mixin notification($notifColor) {
  color: $notifColor;
  font-size: 24px;
  font-weight: bold;
}
.success {
  @include notification(green);
}
.danger {
  @include notification(red);
}
```

### Default Value of Mixin

It is also possible to define default values for mixin variables

```scss
@mixin bordered($color: blue, $width: 1px) {
  border: $width solid $color;
}
.myStyles {
  @include bordered($color: orange);
}
```

## Extend Directive

The @extend directive lets you share a set of CSS properties from one selector to another.

```scss
.button-basic {
  border: none;
  padding: 15px 30px;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
}

.dander-button {
  @extend .button-basic;
  background-color: red;
  color: white;
}

.success-button {
  @extend .button-basic;
  background-color: green;
  color: white;
}
```
