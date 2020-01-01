Simplater
======

Fast, minimalistic, logic-less string templating libray inspired by [mustache](https://mustache.github.io/).

Features:
1. Pure string substitution only. Avoids  [this](https://www.johndcook.com/blog/2011/07/19/you-wanted-banana/).
2. Pure JS & Zero dependencies


Template
---------
Anything surrounded by double braces will be treated as a variable and substituted.

eg. ```{{ param }}```

Example
---------

```
const simplater = require('simplater')

const myTemplate = 'The quick {{colour}} fox jumps over the lazy dog'
console.log(simplater.render(myTemplate, { colour: 'brown' }))

// Output
// The quick brown fox jumps over the lazy dog
```

API
----
render function can take three params

```render (template, params, defaultValue)```

where,

```template``` = template string (if passed value is not a string, null will be returned)

```params``` = object containing different params & its corresponding values

```defaultValue``` (*optional*) = the value to substitute if a particular param in template string is not found in params object passed. If not specified, it defaults to a blank string ''


Notes
------

1. Spaces inside double curly braces are ignored while substituting. eg. ```{{colour}}```, ```{{ colour}}```, ```{{  colour  }}``` will be treated same
2. Nesting is not supported. If by mistake nested values are passed, only innermost value shall be substituted. ```{{ {{ colour }}}}``` will be rendered to ``` {{ brown}}``` (a quick hack to support this case is to call render again).