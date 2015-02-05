# Manage your Go runtime environment with goenv.

<img align="right" src="https://github.com/l3x/goenv/blob/master/gopher-world-small.png">

Use goenv to find, (un)install or switch to a version of Go.

**Easy to use** Use goenv to install a version of Go. Run setup once and
forget about it until you're ready to change your Go runtime version.

It's as light-weight and unobtrusive as it gets.

You can install, and later upgrade goenv using git.

## Table of Contents

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
. goenv 1.3.3                        # To switch to version 1.3.3 (you can use any valid Go version)
. goenv 1.4                          # To switch to version 1.4
```

### Locating the Go Installation

Once goenv has determined which version of Go your application has
specified, it passes the command along to the corresponding Homebrew
install command.

Each Go version is installed into its own directory under
`/usr/local/Cellar/go`. For example, you might have these versions
installed:

* `/usr/local/Cellar/go/1.3.3 (4344 files, 114M) *`
* `/usr/local/Cellar/go/1.4 (4557 files, 134M)`

Note that the "*" at the end of the line indicates the current Go runtime.


## Installation

**Compatibility note**: goenv is not _incompatible_ anything\*\*\*.  You can install
goenv without concern regarding "conflicting software".

\*\*\* goenv assumes you are using a mac (OSX) and have
[Homebrew](#homebrew-on-mac-os-x) installed.

You can choose to install using git or you can install goenv manually.

### Github Installation

This will get you going with the latest version of goenv and make it easy to fork and contribute any changes back upstream.

#### 1) Checkout goenv into ~/.goenv
~~~
$ git clone https://github.com/l3x/goenv.git ~/.goenv
~~~

#### 2) Add `~/.goenv/bin` to your `$PATH` for access to the `goenv` command-line utility.
~~~
$ echo ';export PATH="$HOME/.goenv/bin:$PATH"; if which goenv > /dev/null; then . goenv init; fi' >> ~/.bashrc
~~~

#### 3) Restart your shell so that PATH changes take effect.
(Opening a new terminal tab will usually do it.) Now check if goenv was set up:
~~~
$ goenv version goenv
1.0.0
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


#### 4) Find a verion of Go that you want to install:
~~~
$ goenv versions available
~~~


#### 5) Install Go:
For example, we can choose to install version 1.4...
~~~
$ goenv 1.4
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

To remove old Go versions, run `$ goenv uninstall 1.3.3`

... where 1.3.3 is the version of Go that you want to uninstall.

To see the versions of Go you have installed run `$ goenv versions`

To verify that your Go runtime environment is okay run `$ goenv check`


## References
* [The Go Programming Language](https://golang.org/)
* [Homebrew](http://brew.sh/)
* [Downloading Git](http://git-scm.com/download/mac)


## Command Reference

~~~
Filename:    goenv
Version:     1.0.0

Purpose:     To manage your Go (golang) runtime version(s).

Usage:       goenv [ 1.3.3 | persist | init | setup | info | check | version [goenv] | versions [available] | install | uninstall ]

Assumptions: 1) You have homebrew installed

Notes:
1) Run "goenv check" to verify that the $GOPATH and the current Go runtime version are equivalent.
2) If you call "goenv init", it will create $HOME/.goenv that will have the current Go runtime version number.
3) This script uses brew-versions to install old versions of go.
4) There may be problems if you try to install versions 1.1.2 and below.
5) After running "goenv setup", you need to open a new terminal window (or source the current one).
6) No shims.  No rehashing.  Just plain shell commands and some brew.
7) Author: Lex Sheehan

Examples:
. goenv 1.3.3                        # To switch to version 1.3.3 (you can use any valid Go version)
. goenv 1.4                          # To switch to version 1.4
. goenv perisist                     # To persist your go version in the $HOME/.goenv file
. goenv init                         # To initialize your go environment with the version in the $HOME/.goenv file
goenv setup                          # To install goenv (only need to do once).  Will be active in subsequent shells.
goenv info                           # To display goenv information
goenv help                           # To display goenv help information
goenv check                          # To verify that your go runtime environment is okay
goenv version                        # To get the current go runtime version
goenv version goenv                  # To get the current goenv version
goenv versions                       # To get a list of locally installed Go versions
goenv versions available             # To get a list of available Go versions
goenv install 1.3.3                  # To install version 1.3.3
goenv uninstall 1.3.3                # To uninstall version 1.3.3
~~~

### Version History

**1.0.0** (January 13, 2015)

* Initial public release.

### License

(The MIT license)

Copyright (c) 2015 Lex Sheehan

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
