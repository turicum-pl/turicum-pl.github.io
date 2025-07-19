# Turicum 1.4.0

The release 1.4.0, as of July 18, 2025 is the fourthe release of the Turicum interpreter.
It delivers a few bugfixes and major feature upgrades.

## Closure joining

You can join two closures using the `pass:[f ## g]` operator.

## Currying and Uncurrying

When you specify the arguments to a method, function, closure or macro (callable) using `.(` instead of `(` the function will not be called, but curried.
You can also uncurry a curried callable.