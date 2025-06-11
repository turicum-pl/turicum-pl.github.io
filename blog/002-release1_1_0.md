# Turicum 1.1.0

The release 1.1.0, as of June 10, 2025 is the second release of the Turicum interpreter.
It delivers a few bugfixes and major feature upgrades.

## REPL

Turicum now comes with a full-featured REPL interpreter.
Starting the interpreter with the `-REPL` option will open an interactive prompt where you can type in commands and see the result immediately.

## Program compilation

Turicum can compile the program into a binary format, and later execute the code from the binaries.
It is not a real binary executable, but loading from this format saves the syntactical analysis and some of the extra effort that is usually done when working from the source code.

## Language changes

### `++` and `--` were introduced

In the original release of the language the pre- and, post-increment and decrement operators were deliberately not included.
They do not really fit well Turicum readability philosophy.
These operators are everything but "functional programming".

In this release they are implemented as commands.
They are recognized as "expressions" only when applied on variables.

### Operator assignments

In addition to the usual `=` assignment, you can have now `+=`, `-=` and so on.
All the operators can be use on the left side of an `=` symbol.

### `**` power operation

Languages use `^` or `pass:[**]` as powering operator (or they do not implement it).
Turicum uses `^` as bitwise XOR operator, and `pass:[**]` as powering operator.

### `mut` update

`let` and `mut` are used to define variables with initial values.
`mut` can also be used to update variables when used in the

    mut [...] =

or

    mut {...} =

form.