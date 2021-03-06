# @articulate/progress
[![@articulate/progress](https://img.shields.io/npm/v/@articulate/progress.svg)](https://www.npmjs.com/package/@articulate/progress)
[![Build Status](https://travis-ci.org/articulate/progress.svg?branch=master)](https://travis-ci.org/articulate/progress)
[![Coverage Status](https://coveralls.io/repos/github/articulate/progress/badge.svg?branch=master)](https://coveralls.io/github/articulate/progress?branch=master)
[![NSP Status](https://nodesecurity.io/orgs/articulate/projects/172aa9db-55a1-4f0d-b76e-2408bf81d4fa/badge)](https://nodesecurity.io/orgs/articulate/projects/172aa9db-55a1-4f0d-b76e-2408bf81d4fa)

![@articulate/progress](https://user-images.githubusercontent.com/888052/32856962-53142736-ca14-11e7-8296-90160a1fa221.gif)

Cheap, functional, terminal progress bar.

Next time you're tempted to `process.stderr.write('.')` to track the progress of a script... don't.  Use this instead.

## API

```haskell
progress : Object -> Number -> ()
```

To setup your progress bar, execute the module with an optional options object:

```js
const progress = require('@articulate/progress')({ /* options here */ })
```

The following options are accepted:

| Name | Type | Default | Description |
| ---- | ---- | ------- | ----------- |
| `label` | `String` | `'progress'` | custom label for your progress bar |
| `stream` | `stream.Writable` | `process.stderr` | output stream for progress |
| `width` | `Number` | `24` | max width of the bar |

The returned function accepts a progress ratio between `0` and `1`, and writes the progress bar to the output stream.  Each time it is called, it will overwrite the previous state of the progress to appear animated in the console.

```js
const progress = require('@articulate/progress')()

progress(0.55)
//> progress: ⣠ [==============          ] 55%
```

See [`demo.js`](https://github.com/articulate/progress/blob/master/demo.js) for a slightly more complex example.
