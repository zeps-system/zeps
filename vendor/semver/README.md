# semver

A simple semantic versioning utility for zepto.

## Usage

The interface is akin to [that of npm](https://github.com/npm/node-semver),
albeit much simpler.

````clojure
(import-all "semver" "sv")

(sv:parse "1.1.0") ; will return a semver object
(sv:parse ">1.1.0") ; will also return a semver object, the comparator is preserved
(sv:valid? "10.3.2") ; will return true
(sv:valid? "foo.bar") ; will return false
(sv:gt "1.1.0" "1.0.0") ; will return true
(sv:gt (sv:parse "1.1.0") "1.0.0") ; this will also work
(sv:matches "1.2.0" ">1.1.0") ; will return true - the second argument is the constraint
```

<hr/>

Have fun!
