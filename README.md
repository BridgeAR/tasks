# Tasks

A list of things that I feel would be good to do in Node.js and mainly some
modules.

## Node.js

1. Change the `compact` option default from `true` to `false` in util.inspect
1. In the `assert` module activate the new diffing for error messages for the
   legacy mode.
1. Add a new `util.inspect` option that deactivates checking for special keys on
   Arrays and TypedArrays.
   Follow-up: Open a PR to make the new `util.inspect` option a default.
   Alternative: Open an issue in the V8 bug tracker to improve `Object.keys` and
                or to add a function that behaves like a `Object.arrayKeys`
                function that only returns special keys and not 0-n.
                This is probably not the best idea because it is engine specific.
                The main point would be to make the TC39 realize that this would
                be beneficial to have.
1. Add a new `NODE_COLORS` environment variable to either enforce or deactivate
   color output throughout anything in Node.js core. At the same time the
   `NODE_DISABLE_COLORS` environment variable should be Documentation-only
   deprecated. See also https://github.com/nodejs/node/issues/18175 .

## TC39

1. Add a pattern to try / catch as in:
   `try {} catch[pattern] (err) {} catch (err) {}`.
   Reason: That allows to catch specific error types or maybe error messages /
           regular expressions.
1. Add a `Object.arrayKeys()` to the language.
   Reason: This allows to have a much more efficient way to check if an Array
           or TypedArray has keys besides the regular 0-n. Otherwise this can
           result in a huge performance overhead that is not necessary at all.
