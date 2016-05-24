# zeps

![](http://g.recordit.co/RC7OAMIAXe.gif)

zeps (the **ze**pto **p**ackage **s**ystem) is a package manager for
zepto. It simplifies installing (for package users) and
versioning (for package creators).

## Installation

```sh
git clone https://github.com/hellerve/zeps
zepto zeps/zeps install . --path zeps
```

## Usage

### Installing Packages

The most common task for users will be installing zepto
packages. Packages should either be uploaded and registered
on the [zpr](https://zpr.com) (the **z**epto **p**ackage **r**egistry)
or published on [Github](https::/github.com).

```sh
# Basic usage for installing packages 
zeps install html # this will install the newest version of the html package on zpr
zeps install zepto-lang/html # this will do the same thing, but from Github
zeps install html==1.0.0 # this will install version 1.0.0 of the html package
zeps install . # this will install the module in the current directory
```

Github-installed packages follow the convention of `<owner>/<repo>`.
This means that zpr packages can never contain a slash.

### Registering Packages

Registering packages is only necessary if it should be
put on zpr. Github packages do not need to be registered in that way.
Names on zpr need to be unique when registering. Users wanting
to upgrade packages need to be owners or collaborators.

```sh
# Basic workflow for registering packages on zpr
zeps register html # this will try to register this package under the name html
zeps upgrade html # this will try to upgrade the html package on zpr
```

## The module.zp file

The `module.zp` file contains all necessary meta information
about a package, such as name, version, license etc. For an
exhaustive example, see `examples/package/module.zp`.

<hr/>

Have fun!
