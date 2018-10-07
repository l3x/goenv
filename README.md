# Manage your Go environment with goenv.

<img align="right" src="https://github.com/l3x/goenv/blob/master/gopher-world-small.png">

* Having problems getting your Go source code to build and run?

* Tired of keeping track of which directory is your GOPATH and where to edit your source files?

* Are you a consultant that must manage multiple projects with various Go runtime requirements?

* Want to see how your Go app runs when compiled using various versions of Go?

* Like to keep things simple?

Use goenv to find, (un)install or start using any version of Go.

**Easy to use** 
* Install any version of Go.
* Set any Go project to use any goenv installed version of Go.
* Even helps you cd into your most recently used Go project.

It's as light-weight and unobtrusive as it gets.

## goenv help

```
$ goenv help
Filename:     goenv
Version:      2.0.0
Purpose:      To manage your Go (golang) environment
Copyright:    United Ledger, LLC

Assumptions: 
* You must have  access to the internet and git to install a new Go version.
* Your OS's equivalent of build-essential must also be installed to install Go.
* egrep and standard shell commands like grep, echo, printf and cat must be installed.
* Go must already be installed (via your system package manager).
* The install goenv command adds goenv to your PATH env var in the bashrc file.
* (Move that PATH command appropriately if you are using a shell other than Bash.)

Notes:
* goenv allows you to manage multiple versions of Go.
* No shims. No rehashing. Just plain shell commands.
* goenv version works on linux (likley also works on macOS and Windows).
* You must be in a GOPATH directory to run the set command.
* Source goenv commands that update environment variables. See examples.
* To install goenv: 
* 1) Download this goenv repo and cd into it (where the README.md file is).
* 2) Run this:  ./bin/goenv install goenv
* To uninstall goenv: 
* 1) Remove the PATH export that was appended to your /home/lex/.bashrc
* 2) Remove the /home/lex/.goenv directory

Examples:
  goenv help                        # To print this help info
  goenv install goenv               # To put goenv on your PATH for future logins  
  goenv install go1.9.4             # To install go1.9.4 (or any Go version)
  goenv uninstall go1.9.4           # To uninstall go1.9.4 (or any installed Go version)
  goenv list-installed-versions     # To get a list of installed Go versions
  goenv list-available-versions     # To get a list of available Go versions
  goenv info                        # To print Go environment information
  goenv run-tests                   # To run goenv tests
  . goenv use go1.9.4               # Source and run this to set your Go runtime to go1.9.4
  . goenv install go1.9.5           # To install go1.9.5 and set the Go runtime to go1.9.5
  . goenv set                       # Source and run to set GOPATH, GOBIN and PATH
  . goenv cd                        # Source and run this to cd into your last/current GOPATH
```

## goenv info
```
$ goenv info

 CURRENT GO VERSION:    go version go1.9.5 linux/amd64
 GOENV_HOME:            /home/lex/.goenv
 GOENV_GOROOTS_PATH:    /home/lex/.goenv/goroots
 GOENV_ENV_PATH:        /home/lex/.goenv/.env
 GOENV_SHELL_INIT_FILE: /home/lex/.bashrc
 GOENV_GO_SOURCE_REPO:  https://go.googlesource.com/go
 GOENV_CURRENT_GOPATH:  /home/lex/.goenv/.current_gopath
 $(pwd):                /home/lex/GOPATHs/helloworld
 GOROOT:                /home/lex/.goenv/goroots/go1.9.5
 --- Use set command for following ---
 GOPATH: /home/lex/.goenv/goroots/go1.9.4
 GOBIN:  /home/lex/.goenv/goroots/go1.9.4/bin
 PATH:   
/home/lex/.goenv/goroots/go1.9.5/bin
/home/lex/.goenv/goroots/go1.9.4/bin
/usr/local/bin
/usr/bin
/bin
/usr/local/sbin
/usr/lib/jvm/default/bin
/usr/bin/site_perl
/usr/bin/vendor_perl
/usr/bin/core_perl
~/bin
/home/lex/.goenv/bin

```

## goenv list-installed-versions
```
$ goenv list-installed-versions
/home/lex/.goenv/goroots/go1.11.1
/home/lex/.goenv/goroots/go1.9.5
/home/lex/.goenv/goroots/go1.9.4
```

## goenv list-available-version
```
$ goenv list-available-versions
go1
go1.0.1
go1.0.2
go1.0.3
go1.1
go1.1.1
go1.1.2
go1.10
go1.10.1
go1.10.2
go1.10.3
go1.10.4
go1.10beta1
go1.10beta2
go1.10rc1
go1.10rc2
go1.11
go1.11.1
go1.11beta1
go1.11beta2
go1.11beta3
go1.11rc1
go1.11rc2
go1.1rc2
go1.1rc3
go1.2
go1.2.1
go1.2.2
go1.2rc2
go1.2rc3
go1.2rc4
go1.2rc5
go1.3
go1.3.1
go1.3.2
go1.3.3
go1.3beta1
go1.3beta2
go1.3rc1
go1.3rc2
go1.4
go1.4.1
go1.4.2
go1.4.3
go1.4beta1
go1.4rc1
go1.4rc2
go1.5
go1.5.1
go1.5.2
go1.5.3
go1.5.4
go1.5beta1
go1.5beta2
go1.5beta3
go1.5rc1
go1.6
go1.6.1
go1.6.2
go1.6.3
go1.6.4
go1.6beta1
go1.6beta2
go1.6rc1
go1.6rc2
go1.7
go1.7.1
go1.7.2
go1.7.3
go1.7.4
go1.7.5
go1.7.6
go1.7beta1
go1.7beta2
go1.7rc1
go1.7rc2
go1.7rc3
go1.7rc4
go1.7rc5
go1.7rc6
go1.8
go1.8.1
go1.8.2
go1.8.3
go1.8.4
go1.8.5
go1.8.5rc4
go1.8.5rc5
go1.8.6
go1.8.7
go1.8beta1
go1.8beta2
go1.8rc1
go1.8rc2
go1.8rc3
go1.9
go1.9.1
go1.9.2
go1.9.3
go1.9.4
go1.9.5
go1.9.6
go1.9.7
go1.9beta1
go1.9beta2
go1.9rc1
go1.9rc2
```
