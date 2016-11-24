# request

A minimal request library for and in zepto.
Requires at least version 0.9.2.

## Usage

This library exposes a few endpoints for simple
REST interfaces (seriously, if you need professional-grade
stuff, use something else). Usage looks a little like this.

````clojure
(load "request/request")
(import-all "request")

(request:get "google.com") ; Additionally, you can specify headers as a hash-map
; => a hash-map with the values :body, :headers :status, :version and :message

(request:set-follow-redirects! #t) ; Redirects are followed
(reqest:get "google.com:80")
; => this redirects me to another (the german) google page
```

<hr/>

Have fun!
