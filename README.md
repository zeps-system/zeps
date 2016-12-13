# zeps

![](http://g.recordit.co/RC7OAMIAXe.gif)

zeps (the **ze**pto **p**ackage **s**ystem) is a package manager for
zepto. It simplifies installing (for package users) and
versioning (for package creators). It is in public alpha.

## Installation

```sh
git clone https://github.com/hellerve/zeps
zepto zeps/zeps install . --path zeps
```

If the command zeps is still not found, try prepending `sudo` to the above.

## Usage

### Installing Packages

The most common task for users will be installing zepto
packages. Packages should either be uploaded and registered
on the [zpr](https://zpr.com) (the **z**epto **p**ackage **r**egistry, which is not done yet)
or published on [Github](https::/github.com).

```sh
# Basic usage for installing packages 
zeps install html # this will install the newest version of the html package on zpr
zeps install zepto-lang/html # this will do the same thing, but from Github
zeps install html==1.0.0 # this will install version 1.0.0 of the html package
zeps install . # this will install the module in the current directory
zeps i . # just a little shortcut
```

Github-installed packages follow the convention of `<owner>/<repo>`.
This means that zpr packages can never contain a slash. While we're at it:
A package name can contain any character other than slashes and comparator
characters (so `>`, `=`, `<` and `@` are all not allowed).

### Creating new packages

To make writing new packages as easy as possible zeps comes with a bootstrapping
mechanism. There are currently only two types of templates: `lean`, which will
bootstrap a very basic environment for a software library (available from `hellerve/lean`)
and `tool`, which will create a minimal environment for writing a CLI tool (available from
`hellerve/tool`).

```sh
# How to create a package
zeps new lean my-package # this will create a directory my-package with a few basic files
zeps new tool leatherman # same, but for tools
zeps n tool nunchaku # same, but using a shortcut
```

This highlights two of the three types of packages in zeps - there are tools, libraries
and templates. Tools need an entry-point and installing them means that the package
will then be on your path as a command. Libraries are normal software libraries that
makes writing applications easier for you. Templates are scripts that interface with
zeps directly, like `lean` and `tool` do, to simplify the process of application creation.

### Registering Packages

To be able to register packages you will need to generate a RSA key.
You can either do this manually using the `keygen` command or just be affirmative
when you are prompted whether you want it to be generated automatically for you
by the `register` command.

```sh
# Basic workflow for registering packages on zpr
zeps register . # this will try to register the package on the zpr
zeps register . -g # this will try to register the package on the zpr and create a tag on github so we can find the package revision
```

### Documenting packages

`zeps` can also be used to generate package documentation. If the docstrings
in the documentation file adhere to the format specified below, running the command

```
zeps docgen yourpackage
```

will generate a HTML file that documents all public functions of your package.

The format is as follows:

```
the summary of the documentation. it can be any number of lines and paragraphs.

params:
 - parameter1: each parameter is preceded by a "-" and after a ":", you can describe it
 - parameter2: it need not be the first element below the documentation
complexity: computational complexity, usually denoted in big-O-notation, but can be anything
returns: a description of the return value
```

And that's it!

#### Advanced features

You can actually use HTML for documentation markup (I do not sanity check it, so please don't
abuse it). There are a few special tags, listed below:

- zepto: this tag will highlight the zepto code contained within it (courtesy of [prism](http://prismjs.com/)).
- par: this will link to the function parameter (it should contain the name of the paramete).
- fun: this will link to another function in the documentation (it should contain the name of the function).

## The module.zp file

The `module.zp` file contains all necessary meta information
about a package, such as name, version, license etc. For a fairly
exhaustive example, see `examples/package/module.zp`.

## Overview over all of the commands

```
	test: Runs the module tests.
	t: shortcut for test.
	search: Search for packages matching a search term (on the ZPR).
	sandbox: Create/destroy a sandboxed zeps environment
	run: Run the module entry-point, without installing it
	repl: Launches an interactive shell with a certain module preloaded.
	remove: Removes a package.
	rm: shortcut for remove.
	register: Registers a package.
	r: shortcut for register.
	new: Bootstraps a new package.
	n: Shortcut for new.
	keygen: Generates a new RSA key for zeps.
	install: Installs a package.
	i: Shortcut for install.
	help: Interactive help on getting started (EXPERIMENTAL/BUGGY)
	readme: Prints zeps' README
	docgen: Generate documentation for a package from its docstrings
	doc: Format and print documentation for package or function
```

<hr/>

Have fun!
