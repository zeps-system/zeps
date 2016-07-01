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

## The module.zp file

The `module.zp` file contains all necessary meta information
about a package, such as name, version, license etc. For a fairly
exhaustive example, see `examples/package/module.zp`.

## Overview over all of the commands

```
	upgrade: Upgrades a package.
	up: shortcut for upgrade.
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
```

<hr/>

Have fun!
