# Manage your Go runtime environment with goenv.

<img align="right" src="https://github.com/l3x/goenv/blob/master/gopher-world-small.png">

Use goenv to find, (un)install or switch to any version of Go.

**Easy to use** You can set any Go project to use any goenv installed version of Go

It's as light-weight and unobtrusive as it gets.

```
$ goenv help
Filename:     goenv
Version:      2.0.0
Purpose:      To manage your Go (golang) runtime version(s).
Copyright:    United Ledger, LLC

Assumptions: 
* You must have  access to the internet and git to install a new Go version.
* Your OS's equivalent of build-essential must also be installed to install Go.
* The rmrf script is in your PATH (used in install and uninstall commands)
* egrep must be installed.
* Go must already be installed (via your system package manager)

Notes:
* goenv allows you to manage multiple versions of Go.
* No shims. No rehashing. Just plain shell commands.
* Current version works on linux. (Should work on macOS and Windows).
* Source goenv when you want it to update environment variables.

Examples:
  goenv help                        # To print this help info
  goenv install go1.9.4             # To install go1.9.4 (or any Go version)
  goenv uninstall go1.9.4           # To uninstall go1.9.4 (or any installed Go version)
  goenv list-installed-versions     # To get a list of installed Go versions
  goenv list-available-versions     # To get a list of available Go versions
  goenv info                        # To print goenv environment variable
  goenv run-test                    # To run goenv tests
  . goenv use go1.9.4               # Source and run this to set your go runtime to go1.9.4
  . go-env set-current-gopath       # Source and run this when you're in your project's gopath

```


### License

(The MIT license)

Copyright (c) 2018 United Ledger LLC

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
