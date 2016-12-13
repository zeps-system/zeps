# mustache

A minimal templating engine in and for zepto.
It is a [mustache](http://mustache.github.com) port (no lambdas and custom delimiters, otherwise complete to my best of knowledge).

The package documentation can be found in `docs/index.html`
or generated via zeps' `docgen` command.

## Installation

```
zeps install zepto-lang/mustache
```

## Usage

There is a single endpoint at the moment, called `template`:
```clojure
(load "mustache/mustache")
(define template (import "mustache:template"))
; Here is an example from the test suite;
; sorry for those weird linebreaks, they are supposed to make this readable (i know it's still a mess)
(minitest:assert-equal
  "
<h1>I am a title</h1>
<span>I am some text</span>
<ul><li>We</li><li>Are</li><li>Elements</li></ul>"
  (template
    "
<h1>{{#render-title}}I am a title{{/render-title}}{{^omit-closing}}</h1>{{/omit-closing}}
{{{text}}}
<ul>{{#elements}}<li>{{.}}</li>{{/elements}}</ul>"
    #{"render-title" #t
      "omit-closing" #f
      "text" "<span>I am some text</span>"
      "elements" ("We" "Are" "Elements")})
  "A silly, but somewhat complete example")
```

The test suite is surprisingly somewhat complete.

<hr/>
Have fun!
