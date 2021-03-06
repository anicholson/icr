# ICR - Interactive Crystal [![Build Status](https://travis-ci.org/crystal-community/icr.svg?branch=master)](https://travis-ci.org/crystal-community/icr)

Interactive console for [Crystal Programming Language](http://crystal-lang.org/).

* [Usage](#usage)
  * [Require local files](#require-local-files)
* [Installation](#installation)
  * [Arch Linux](#arch-linux)
* [How does it work?](#how-does-it-work)
* [Commands and special locals](#commands-and-special-locals)
* [Update check](#update-check)
* [Development](#development)
* [Editor Integration](#editor-integration)
* [Contributors](#contributors)

## Usage

It's like irb, but for Crystal:

![GIF demo](https://raw.githubusercontent.com/crystal-community/icr/master/demo/demo.gif)

### Require local files
You can require local files by relative path (starts with `./`):
```
require "./src/my_cool_lib"
```

Libs can also be required from the cli:

```
$ icr -r colorize -r ./src/my_cool_lib
```

## Installation
Prerequisites:
* The latest version of crystal.
* Readline (for Debian/Ubuntu install `libreadline6-dev` package).
* LLVM development files.

Clone the repo:
```
git clone https://github.com/crystal-community/icr.git
```
Switch to repo-directory:
```
cd icr
```
Build:
```
make
```
And create symlink of `./bin/icr` in to direcotory that is listed in your `$PATH`, e.g.:
```
sudo ln -s $(realpath ./bin/icr) /usr/local/bin/icr
```
_(it's necessary only for the first time)_

### As a shard dependency

If you would like to include icr as a dependency, you can add it to your `shard.yml`

```yml
dependencies:
  icr:
    github: crystal-community/icr
    branch: master
```

Then just run `shards install` from your project!

Enjoy!


### Arch Linux

Arch Linux users can install ICR [from AUR](https://aur.archlinux.org/packages/crystal-icr/).


## How does it work?
* Every time you press `Enter` it adds a new instruction, generates a new crystal program, and executes it.
* The output is split into 2 parts: regular program output (e.g. output from `puts 10`) and the value returned by the last command.
* The regular output is saved, and when you type a new instruction, a new program is generated. The saved output is subtracted from the new output, and the difference is printed out. It creates an illusion that only new instructions are executed :)

## Commands and special locals

* `paste` - enables paste mode
* `debug` - toggles debug mode off and on. In debug mode icr will print the code before executing it
* `quit` or `exit` - exits current interactive console
* `reset` - clears out all of the accumulated commands
* `__` - holds the result of the last expression. Example:

```crystal
icr > "5" + "2"
=> "52"
icr > __.to_i - 10
=> 42

```

## Update check

ICR periodically checks for the new releases on Github. If your current version is out of date, it will simply show you a notice at start.

You can disable this behavior using `--disable-update-check` CLI flag.

## Development

To run tests:
```
make test
```

## Editor integration

 - [inf-crystal.el](https://github.com/brantou/inf-crystal.el) - Connects REPL buffer to the ICR subprocess in Emacs

## Contributors

- [greyblake](https://github.com/greyblake) Potapov Sergey - creator, maintainer
- [BlaXpirit](https://github.com/BlaXpirit) Oleh Prypin - fixes for Crystal 0.16
- [puppetpies](https://github.com/puppetpies) Brian Hood - support of records
- [jwoertink](https://github.com/jwoertink) Jeremy Woertink - support of -r option and number of other contributions
- [veelenga](https://github.com/veelenga) V. Elenhaupt - maintenance
- [MakeNowJust](https://github.com/MakeNowJust) TSUYUSATO Kitsune - syntax highlight support
