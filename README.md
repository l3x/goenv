# Manage your Go runtime environment with goenv.

<img align="right" src="https://github.com/l3x/goenv/blob/master/gopher-world-small.png">

Use goenv to find, (un)install or switch to a version of Go.

**Easy to use** Use goenv to install a version of Go. Run setup once and
forget about it until you're ready to change your Go runtime version.

It's as light-weight and unobtrusive as it gets.

You can install, and later upgrade goenv using git.

```
$ goenv help
Filename:     goenv
Version:      2.0.1
Purpose:      To manage your Go (golang) runtime version(s).
Copyright:    United Ledger, LLC

Assumptions: 
* You must have  access to the internet and git to install a new go version.
* Your OS's equivalent of build-essential must also be installed to install go.
* The rmrf script is in your PATH (used in install and uninstall commands)
* egrep must be installed.

Notes:
* No shims. No rehashing. Just plain shell commands.
* Current version works on linux. 

Examples:
  goenv install go1.9.4             # To install go1.9.4
  goenv uninstall go1.9.4           # To uninstall go1.9.4
  goenv list-go-installed-versions  # To get a list of installed Go versions
  goenv list-go-available-versions  # To get a list of available Go versions
  goenv info                        # To golang info
  goenv print-env-vars              # To goenv environment variables
  goenv run-test                    # To run goenv tests
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
