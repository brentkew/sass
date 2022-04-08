# sass
* [Introduction](#Introduction)
* [Why to Use SASS](#why-to-use-sass)
* [SASS Variables](#sass-variables)
* [SASS Variable Scope](#sass-variable-scope)


## Introduction
SASS stand for (Syntactically Awesome Stylesheet) is a CSS per-processor,
which helps to reduce repetition in CSS.

It was initially designed by **Hampton Catlin** and developed by **Natalie 
Weizenbaum** in 2006. Later, Weizenbaum and Chris Eppstein 
used its initial version to extend the Sass with SassScript. 

## Why to Use SASS ?
   * It is pre processor language which provide indented syntax for CSS.
   * It provides some features that allows to writing code more efficient
   and reusable manners.
   * It is a super set of CSS, means its contains all the features for CSS
   and it is open source.
   * It allows writing CSS in programming construct.
   
**_A browser does not support SASS code. Therefore we need SASS pre-processor
to convert SASS into standard CSS_**

SASS file has a extension **.sass**

```sass
$primaryColr: #365985
$secondayColr: #741258

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

* String
* Numbers
* Colors
* Booleans
* List
* Nulls

**_SASS uses $ symbol to declared a variable_**

```sass
$myFont: 'Helvetica, sans-serif'
$containerWidth: 300px
$themeColor: 'red'
$bodyFontSize: '12px'

body {
    font-family: $myFont
    font-size: $bodyFontSize
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
practice to defined all global variables in saperate file like _global.scss and 
inclued the file with @include keyword**