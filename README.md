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
1. The `fs` module currently has problems showing the stack trace in async
   functions. This should be addressed to throw them in JS so they have stack
   traces and the proper error code.
   Note: this is something actively developed on and could cause conflicts.
1. Deprecate using Arrays for http headers. For reference:
   https://github.com/nodejs/node/pull/16568
1. Fix wrong error codes. Right now error codes in Node.js often have the wrong
   type and or the wrong error code. There are a couple of comments in
   `internal/errors.js` about it.
1. Consolidate error codes when they are redundant to other error codes.
1. Add a proper description about how collaborators should handle PRs.
   - They should start a CI after creating a own PR.
   - The first person to review a PR that did not yet have a CI should start
     one.
   - If a PR has no outstanding comments, the PR exists for the minimum time
     and it got multiple LGs, instead of just adding another LG, land the PR.
   - If a PR has a CI started and no outstanding comments, at least one LG
     add the `ready` label.
   - If a PR is semver-major a CITGM should be started when a CI is started.
1. Add a `contains` function to the `util` module. It should work similar to
   `util.isDeepStrictEqual` but return true in case `a` is in `b`.
1. Add a option to `util.isDeepStrictEqual` to pass in a `range` option.
   In case numbers are compared this range is allowed as divergent to the real
   number.
1. Add a eslint rule to verify that all existing error codes are actually used
   throughout the code base.
1. Add a `group` property to all Node.js errors. That way it should be possible
   to group error codes that are actually e.g. all network related.

## TC39

1. Add a pattern to try / catch as in:
   `try {} catch[pattern] (err) {} catch (err) {}`.
   Reason: That allows to catch specific error types or maybe error messages /
           regular expressions.
1. Add a `Object.arrayKeys()` to the language.
   Reason: This allows to have a much more efficient way to check if an Array
           or TypedArray has keys besides the regular 0-n. Otherwise this can
           result in a huge performance overhead that is not necessary at all.
