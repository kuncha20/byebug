# Byebug

[![Ver][gem]][gem_url]
[![Gpa][gpa]][gpa_url]
[![Dep][dep]][dep_url]
[![Cov][cov]][cov_url]
[![Git][tip]][tip_url]

[gem]: https://img.shields.io/gem/v/byebug.svg
[gpa]: https://img.shields.io/codeclimate/github/deivid-rodriguez/byebug.svg
[dep]: https://img.shields.io/gemnasium/deivid-rodriguez/byebug.svg
[cov]: https://img.shields.io/codeclimate/coverage/github/deivid-rodriguez/byebug.svg
[tip]: https://img.shields.io/gittip/deivid-rodriguez.svg

[gem_url]: https://rubygems.org/gems/byebug
[gpa_url]: https://codeclimate.com/github/deivid-rodriguez/byebug
[dep_url]: https://gemnasium.com/deivid-rodriguez/byebug
[cov_url]: https://codeclimate.com/github/deivid-rodriguez/byebug
[tip_url]: https://www.gittip.com/deivid-rodriguez

_Debugging in Ruby 2_

Byebug is a simple to use, feature rich debugger for Ruby 2. It uses the new
TracePoint API for execution control and the new Debug Inspector API for call
stack navigation, so it doesn't depend on internal core sources. It's developed
as a C extension, so it's fast. And it has a full test suite so it's reliable.

It allows you to see what is going on _inside_ a Ruby program while it executes
and offers many of the traditional debugging features such as:

* Stepping: Running your program one line at a time.
* Breaking: Pausing the program at some event or specified instruction, to
examine the current state.
* Evaluating: Basic REPL functionality, although [pry][] does a better job at
that.
* Tracking: Keeping track of the different values of your variables or the
different lines executed by your program.


## Build Status

Linux & OSX [![Tra][tra]][tra_url]

Windows [![Vey][vey]][vey_url]

[tra]: https://img.shields.io/travis/deivid-rodriguez/byebug.svg
[vey]: https://ci.appveyor.com/api/projects/status/github/deivid-rodriguez/byebug?svg=true

[tra_url]: https://travis-ci.org/deivid-rodriguez/byebug
[vey_url]: https://ci.appveyor.com/project/deivid-rodriguez/byebug


## Requirements

* Required: MRI 2.0.0 or higher. For debugging ruby 1.9.3 or older, use
[debugger][].

* Recommended:
  - MRI 2.0.0-p576 or higher.
  - MRI 2.1.3 or higher.
  - MRI 2.2.0-preview1 or higher.


## Install

    $ gem install byebug


## Usage

Simply drop

    byebug

wherever you want to start debugging and the execution will stop there. If you
are debugging rails, start the server and once the execution gets to your
`byebug` command you will get a debugging prompt.

Former [debugger][] or [ruby-debug][] users, notice:

* Some gems (rails, rspec) implement debugging flags (-d, --debugger) that early
require and start the debugger. These flags are a performance penalty and byebug
doesn't need them anymore so my recommendation is not to use them. In any case,
both rails and rspec have deprecated these flags in their latest versions.  
* The startup configuration file is now called `.byebugrc` instead of
`.rdebugrc`.


## Byebug's commands

    Command     | Aliases      | Subcommands
    ----------- |:------------ |:-----------
    `backtrace` | `bt` `where` |
    `break`     |              |
    `catch`     |              |
    `condition` |              |
    `continue`  |              |
    `delete`    |              |
    `disable`   |              | `breakpoints` `display`
    `display`   |              |
    `down`      |              |
    `edit`      |              |
    `enable`    |              | `breakpoints` `display`
    `finish`    |              |
    `frame`     |              |
    `help`      |              |
    `history`   |              |
    `info`      |              | `args` `breakpoints` `catch` `display` `file` `files` `line` `program`
    `irb`       |              |
    `kill`      |              |
    `list`      |              |
    `method`    |              | `instance`
    `next`      |              |
    `p`         | `eval`       |
    `pp`        |              |
    `pry`       |              |
    `ps`        |              |
    `putl`      |              |
    `quit`      | `exit`       |
    `reload`    |              |
    `restart`   |              |
    `save`      |              |
    `set`       |              | `autoeval` `autoirb` `autolist` `autoreload` `autosave` `basename` `callstyle` `forcestep` `fullpath` `histfile` `histsize` `linetrace` `tracing_plus` `listsize` `post_mortem` `stack_on_error` `testing` `verbose` `width`
    `show`      |              | `autoeval` `autoirb` `autolist` `autoreload` `autosave` `basename` `callstyle` `forcestep` `fullpath` `histfile` `histsize` `linetrace` `tracing_plus` `listsize` `post_mortem` `stack_on_error` `testing` `verbose` `width`
    `skip`      |              |
    `source`    |              |
    `step`      |              |
    `thread`    |              | `current` `list` `resume` `stop` `switch`
    `tracevar`  |              |
    `undisplay` |              |
    `up`        |              |
    `var`       |              | `all` `class` `constant` `global` `instance` `local`


## Semantic Versioning

Byebug tries to follow [semantic versioning](http://semver.org) and tries to
bump major version only when backwards incompatible changes are released.
Backwards compatibility is targeted to [pry-byebug][] and any other plugins
relying on `byebug`.


## Getting Started

Read [byebug's markdown
guide](https://github.com/deivid-rodriguez/byebug/blob/master/GUIDE.md) to get
started. Proper documentation will be eventually written.


## Related projects

* [pry-byebug][] adds `next`, `step`, `finish`, `continue` and `break` commands
to `pry` using `byebug`.
* [ruby-debug-passenger][] adds a rake task that restarts Passenger with Byebug
connected.
* [minitest-byebug][] starts a byebug session on minitest failures.
* [sublime_debugger][] provides a plugin for ruby debugging on Sublime Text.


## Contribute

See [Getting Started with Development](CONTRIBUTING.md).


## Credits

Everybody who has ever contributed to this forked and reforked piece of
software, specially:

* @ko1, author of the awesome TracePoint API for Ruby.
* @cldwalker, [debugger][]'s mantainer.
* @denofevil, author of [debase][], the starting point of this.
* @kevjames3 for testing, bug reports and the interest in the project.
* @FooBarWidget for working and helping with remote debugging.

[debugger]: https://github.com/cldwalker/debugger
[pry]: https://github.com/pry/pry
[ruby-debug]: https://github.com/mark-moseley/ruby-debug
[debase]: https://github.com/denofevil/debase
[pry-byebug]: https://github.com/deivid-rodriguez/pry-byebug
[ruby-debug-passenger]: https://github.com/davejamesmiller/ruby-debug-passenger
[minitest-byebug]: https://github.com/kaspth/minitest-byebug
[sublime_debugger]: https://github.com/shuky19/sublime_debugger
