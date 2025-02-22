# plisp-mode - Major mode for PicoLisp programming

*Author:* Alexis <flexibeast@gmail.com> (plisp-mode.el); Guillermo R. Palavecine <grpala@gmail.com>, Thorsten Jolitz <tjolitz@gmail.com>, Alexis <flexibeast@gmail.com> (inferior-plisp.el)<br>
*URL:* [https://github.com/flexibeast/plisp-mode](https://github.com/flexibeast/plisp-mode)<br>

`plisp-mode` provides a major mode for PicoLisp programming.

The `plisp-mode` in this package has been built from scratch, and
is not based on, nor connected with, the PicoLisp support for Emacs
provided in [the PicoLisp
distribution](http://software-lab.de/down.html), or the more
recently [updated version of that
support](https://github.com/tj64/picolisp-mode). At this stage, the
main advantages provided by this package are:

* an actively maintained and supported system;

* access to the PicoLisp reference documentation, including via
  Eldoc;

* basic Imenu support;

* ease of customisability; and

* a cleaner codebase.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
 - [Syntax highlighting](#usage-highlighting)
 - [REPL](#repl)
 - [Org Babel](#usage-org-babel)
 - [Documentation](#documentation)
 - [Commenting](#commenting)
 - [Indentation](#indentation)
 - [Miscellaneous](#miscellanous)
- [TODO](#todo)
- [Issues](#issues)
- [License](#license)

## Features

* Syntax highlighting of PicoLisp code. (But please read the below
  [note on syntax highlighting](#note-highlighting).)

* Comint-based `pil` REPL buffers.

* Quick access to documentation for symbol at point.

## Installation

Install [plisp-mode from
MELPA](http://melpa.org/#/plisp-mode), or put the
`plisp-mode` folder in your load-path and do a `(require
'plisp-mode)`.

## Usage

<a name='usage-highlighting'></a>

### Syntax highlighting

Enable syntax highlighting for a PicoLisp source buffer with `M-x
plisp-mode'.

### REPL

Start a `pil` REPL session with <kbd>M-x plisp-repl</kbd> or, from a
`plisp-mode` buffer, with <kbd>C-c C-r</kbd> (`plisp-repl`).

<a name='usage-org-babel'></a>

### Org Babel

Support for Org Babel sessions is available via the
`inferior-plisp` feature, a fork of the [`inferior-picolisp`
library written by Guillermo Palavecino and Thorsten
Jolitz](https://github.com/tj64/picolisp-mode/), stripped down to
only provide the minimum necessary for Org Babel session support,
and modified to be compatible with this package.

Load it with `(require 'inferior-plisp)`, or add
`(inferior-plisp-support-ob-picolisp)` to your init file, and make
sure the `org-babel-picolisp-cmd` variable defined by `ob-picolisp`
is correctly specified for your system.

By default, `inferior-plisp` provides the feature
`inferior-picolisp` required by `ob-picolisp`. To use another
package to provide `inferior-picolisp`, set the
`inferior-plisp-provide-inferior-picolisp` variable to `nil`.

### Documentation

Access documentation for the function at point with <kbd>C-c C-d</kbd>
(`plisp-describe-symbol`). By default, documentation will be
displayed via the `lynx` HTML browser. However, one can set the
value of `plisp-documentation-method` to either a string
containing the absolute path to an alternative browser, or - for
users of Emacs 24.4 and above - to the symbol
`plisp--shr-documentation`; this function uses the `shr` library
to display the documentation in an Emacs buffer. The absolute path
to the documentation is specified via
`plisp-documentation-directory`, and defaults to
`/usr/share/doc/picolisp/`.

Eldoc support is available.

If for some reason the PicoLisp documentation is not installed on
the system, and cannot be installed, setting
`plisp-documentation-unavailable` to `t` will prevent
`plisp-mode` from trying to provide documentation.

### Commenting

Comment a region in a `plisp-mode` buffer with <kbd>C-c C-;</kbd>
(`plisp-comment-region`); uncomment a region in a
`plisp-mode` buffer with <kbd>C-c C-:</kbd>
(`plisp-uncomment-region`). By default one '#' character is
added/removed; to specify more, supply a numeric prefix argument to
either command.

### Indentation

Indent a region in a `plisp-mode` buffer with <kbd>C-c M-q</kbd>
(`plisp-indent-region`). Indentation is done via the `pilIndent`
script provided with the current PicoLisp distribution; the path to
the script is specified via the `plisp-pilindent-executable`
variable.

### Miscellaneous

SLIME users should read the below [note on SLIME](#note-slime).

The various customisation options, including the faces used for
syntax highlighting, are available via the `plisp`
customize-group.

<a name="note-highlighting"></a>

### A note on syntax highlighting

PicoLisp's creator is opposed to syntax highlighting of symbols in
PicoLisp, for [good
reasons](http://www.mail-archive.com/picolisp@software-lab.de/msg05019.html). However,
some - such as the author of this package! - feel that, even taking
such issues into consideration, the benefits can outweigh the
costs. (For example, when learning PicoLisp, it can be useful to
get immediate visual feedback about unintentionally redefining a
PicoLisp 'builtin'.) To accommodate both views, syntax highlighting
can be enabled or disabled via the `plisp-syntax-highlighting-p`
variable; by default, it is set to `t` (enabled).

<a name="note-slime"></a>

### A note on [SLIME](https://github.com/slime/slime)

The design of SLIME is such that it can override `plisp-mode`
functionality. (The documentation for
`plisp--disable-slime-modes` provides details.) The
user-customisable variable `plisp-disable-slime-p` specifies
whether to override these overrides, and defaults to `t`.

## TODO

* Fix misalignment of single-'#' comments upon newline.

<a name="issues"></a>

## Issues / bugs

If you discover an issue or bug in `plisp-mode` not already
noted:

* as a TODO item, or

* in [the project's "Issues" section on
  GitHub](https://github.com/flexibeast/plisp-mode/issues),

please create a new issue with as much detail as possible,
including:

* which version of Emacs you're running on which operating system,
  and

* how you installed `plisp-mode`.

## License

[GNU General Public License version
3](http://www.gnu.org/licenses/gpl.html), or (at your option) any
later version.


---
Converted from `plisp-mode.el` by [*el2markdown*](https://github.com/Lindydancer/el2markdown).
