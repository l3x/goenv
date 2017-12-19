# Manage your Go runtime environment with goenv.

<img align="right" src="https://github.com/l3x/goenv/blob/master/gopher-world-small.png">

Use goenv to find, (un)install or switch to a version of Go.

**Easy to use** Use goenv to install a version of Go. Run setup once and
forget about it until you're ready to change your Go runtime version.

It's as light-weight and unobtrusive as it gets.

You can install, and later upgrade goenv using git.

Note:  goenv (version 1.1.1) currently supports golang 1.4, 1.5, and 1.6


## Table of Contents

* [Info Example](#info-example)
* [Why Use goenv](#why-use-goenv)
* [How It Works](#how-it-works)
* [Understanding PATH](#understanding-path)
* [Choosing the Go Version](#choosing-the-go-version)
* [Locating the Go Installation](#locating-the-go-installation)
* [Installation](#installation)
* [Basic GitHub Checkout](#basic-github-checkout)
* [Upgrading](#upgrading)
* [Homebrew on Mac OS X](#homebrew-on-mac-os-x)
* [Installing Go Versions](#installing-go-versions)
* [Uninstalling Go Versions](#uninstalling-go-versions)
* [Command Reference](#command-reference)
* [Version History](#version-history)
* [License](#license)


## Info Example

This is the what you might see when you ask for info:

<img align="right" src="https://github.com/l3x/goenv/blob/master/goenv-info.png">


## Why Use goenv

If you develop on a mac, you should be using homebrew to manage your OSX apps.

IMHO - Golang should be yet another homebrew managed OSX app.

So, if you have to support golang projects that depend on different go versions
then goenv will help you by making installing golang, switching versions and
managing your go versions within the confines of homebrew.

If you always only ever run the latest version of go, then you might consider
not using goenv and opt to follow these instructions: https://golang.org/doc/install

## How It Works

Setup installs a tiny file $HOME/.goenv that stores the most recently used
version of Go.  Your startup file, e.g., $HOME/.bashrc, will call goenv init
to set Go to the last version you used.  After that, when you want to switch
your Go version just source goenv.  


### Understanding Source

When you "source" a command you preface the command with "source" (or ".")
That tells your shell to run it in the same shell environment that other
commands in your terminal are run.  This way, when goenv can modify your GOROOT
environment variable.

goenv commands that require you to source them include:

* goenv < version.number >
* goenv persist
* goenv init

### Understanding PATH

When you run a command like `ruby` or `brew`, your operating system
searches through a list of directories to find an executable file with
that name. This list of directories lives in an environment variable
called `PATH`, with each directory in the list separated by a colon:

/usr/local/bin:/usr/bin:/bin

Directories in `PATH` are searched from left to right, so a matching
executable in a directory at the beginning of the list takes
precedence over another one at the end. In this example, the
`/usr/local/bin` directory will be searched first, then `/usr/bin`,
then `/bin`.

Just make sure goenv is in your PATH by copying to a directory in your PATH.



### Choosing the Go Version

Execute goenv < version.number > to switch to a different Go version

Examples:
```
. goenv 1.4                        # To switch to latest version of golang 1.4
. goenv 1.5                        # To switch to latest version of golang 1.5
```

### Locating the Go Installation

Once goenv has determined which version of Go your application has
specified, it passes the command along to the corresponding Homebrew
install command.

Previously, each Go version is installed into its own directory under
`/usr/local/Cellar/go`. For example, you might have these versions
installed:

Installed Go versions:

```
/usr/local/Cellar/go/1.4.3 (28B)
/usr/local/Cellar/go/1.5.4 (28B) *
/usr/local/Cellar/go/1.6.2 (5,778 files, 325.3M)
```

Note that the "*" at the end of the line indicates the current Go runtime.

However, things have changed and legacy golang versions have their own brew.

Now, legacy golang versions have their own Cellar install path and a soft
link will be created in the /usr/local/Cellar/go directory.

## Installation

**Compatibility note**: genv is non-invasive and has no adverse side-effects.
You can install goenv without concern regarding "conflicting software".

\*\*\* goenv assumes you are using a mac (OSX) and have
[Homebrew](#homebrew-on-mac-os-x) installed.

You can choose to install using git or you can install goenv manually.

### Github Installation

This will get you going with the latest version of goenv and make it easy to fork and contribute any changes back upstream.

#### 1) Checkout goenv into ~/.goenv
~~~
$ git clone https://github.com/l3x/goenv.git ~/.goenv
~~~

#### 2) Add the following to your  ~/.bashrc file:
~~~
export PATH="$PATH:$HOME/.goenv/bin"
~~~

#### 3) Restart your shell so that PATH changes take effect.
(Opening a new terminal tab will usually do it.) Now check if goenv was set up:
~~~
$ goenv version goenv
1.1.1
~~~


### Manual Installation

Copy the goenv script file to any directory in your PATH and make sure it's
executable.

#### 1) Get a list of directories in your path:
~~~
$ echo "$PATH"|tr ":" "\n"
~~~


#### 2) Copy goenv to any one of those directories:
For example...
~~~
$ cp goenv /usr/local/bin/
~~~


#### 3) Make goenv executable:
~~~
$ chmod +x goenv
~~~


#### 4) Find a version of Go that you want to install:
~~~
$ goenv versions available
~~~


#### 5) Install Go:
For example, we can choose to install version 1.4...
~~~
$ goenv install 1.4
~~~


#### 6) Setup goenv:
~~~
$ goenv setup
~~~


Now, it's all setup and you never have to run goenv setup again.


#### Upgrading

If you've installed rbenv manually using git, you can upgrade your
installation to the cutting-edge version at any time.

~~~ sh
$ cd ~/.goenv
$ git pull
~~~

To use a specific release of rbenv, check out the corresponding tag:

~~~ sh
$ cd ~/.goenv
$ git fetch
$ git checkout v1.0.1
~~~


### Homebrew on Mac OS X

You must have homebrew installed.  And you must have Go installed before
installing homebrew.

~~~
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew update
$ brew doctor
~~~

Afterwards you'll still need to add `eval "$(rbenv init -)"` to your
profile as stated in the caveats. You'll only ever have to do this
once.


### Installing Go Versions

You already know how to do this.  See steps #4 and #5 above.


### Uninstalling Go Versions

As time goes on, Go versions you install will accumulate in your
`/usr/local/Cellar/go/` directory.

To remove old Go versions, run `$ goenv uninstall 1.4`

... where 1.4 is the version of Go that you want to uninstall.

To see the versions of Go you have installed run `$ goenv versions`

To verify that your Go runtime environment is okay run `$ goenv check`

## Global GOPATH v. Project GOPATH

### Global GOPATH

Most sources only discuss GOPATH in terms of a global path.

If this is what you choose, then it's a good idea to put the following in a startup file, e.g., ~/.bashrc

```
export GOPATH=$HOME/go
export PATH=$PATH:$GOPATH/bin
```

Most sources also suggest we use `go get` to grab the latest version of packages.

#### Download package

```
go get -d github.com/dancannon/gorethink
```

#### Download and update package references

```
go get -u github.com/dancannon/gorethink
```

### Project GOPATH

If you choose to use per-project settings then you'll likely want to use something like Glide.

To make things easier, I created an init script that creates some frequently used aliases.

For details on how this works, see the appendix in my book [Learning Functional Programming in Go](amazon.com/Learning-Functional-Programming-Lex-Sheehan-ebook/dp/B0725B8MYW)

Using the "Dot Init" method, we can have per-project GOPATH and modern per-project dependency management.

## References
* [The Go Programming Language](https://golang.org/)
* [Homebrew](http://brew.sh/)
* [Downloading Git](http://git-scm.com/download/mac)


## Command Reference

~~~
Filename:    goenv
Version:     1.1.1

Purpose:     To manage your Go (golang) runtime version(s).

Usage:       goenv [ 1.4.3 | 1.5.4 | 1.6.2 | persist | init | setup | info | check | version [goenv] | versions [available] | install 1.4 | install 1.5 | install 1.6 | uninstall 1.4 | uninstall 1.5 | uninstall 1.6 ]

Assumptions: 1) You have homebrew installed

Notes:
1) Run "goenv check" to verify that the $GOPATH and the current Go runtime version are equivalent.
2) If you call "goenv init", it will create $HOME/.goenv that will have the current Go runtime version number.
3) After running "goenv setup", you need to open a new terminal window (or source the current one).
4) No shims.  No rehashing.  Just plain shell commands and some brew.
5) Author: Lex Sheehan

Examples:
  . goenv 1.4.3                        # To switch to latest version of golang 1.4
  . goenv 1.5.4                        # To switch to latest version of golang 1.5
  . goenv 1.6.2                        # To switch to latest version of golang 1.6
  . goenv perisist                     # To persist your go version in the $HOME/.goenv file
  . goenv init                         # To initialize your go environment with the version in the $HOME/.goenv file
  goenv setup                          # To install goenv (only need to do once).  Will be active in subsequent shells.
  goenv info                           # To display goenv information
  goenv help                           # To display goenv help information
  goenv check                          # To verify that your go runtime environment is okay
  goenv version                        # To get the current go runtime version
  goenv version goenv                  # To get the current goenv version
  goenv versions available             # To get a list of available Go versions
  goenv install 1.4                    # To install latest version of golang 1.4
  goenv uninstall 1.4                  # To uninstall latest version of golang 1.4
  goenv install 1.5                    # To install latest version of golang 1.5
  goenv uninstall 1.5                  # To uninstall latest version of golang 1.5
  goenv install 1.6                    # To install latest version of golang 1.6
  goenv uninstall 1.6                  # To uninstall latest version of golang 1.6
~~~

### How To Install Latest Version of Go on Your Mac

This shows that your current $GOROOT is pointing to an old version of Go that is no longer installed on your mac:

```
$ goenv info
STATUS: ERROR:  Go command not found.
TIP: Don't forget to source goenv when running goenv commands that change your Go version (For more info run $ goenv info)
GOROOT: /usr/local/Cellar/go/1.6.2/libexec
GOPATH: /Users/lex/dev/go
GOBIN : /Users/lex/dev/go/bin
GOOS  : darwin
GOARCH: amd64
Current Go version:
Latest Brew Go version file: /Users/lex/.goenv/lastest-brew-go-version
Latest Brew Go version     :
switchtogo version file: /Users/lex/.goenv/version
switchtogo version     : 1.7.3
goenv version: 1.1.1
Installed Go versions:
/usr/local/Cellar/go/1.7.3 (6,438 files, 250.6M) *
```

Run this to install the latest version of Go (version 1.7.4_2 currently)
```
$ brew upgrade go
```

Now, you've got the latest version of Go installed (and the install is managed by homebrew).

<img src="https://github.com/l3x/goenv/blob/master/latest-go-ver-174.png">


### Version History

```
**1.1.1** (July 11, 2016)
**1.1.0** (July 11, 2016)
**1.0.0** (January 13, 2015)
```

* Initial public release.

### License

(The MIT license)

Copyright (c) 2015, 2016 Lex Sheehan

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
  "Software"), to deal in the Software without restriction, including
  without limitation the rights to use, copy, modify, merge, publish,
  distribute, sublicense, and/or sell copies of the Software, and to
  permit persons to whom the Software is furnished to do so, subject to
  the following conditions:

  The above copyright notice and this permission notice shall be
  included in all copies or substantial portions of the Software.

  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
  EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
  MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
  NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
  LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION
  OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION
  WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
