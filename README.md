This package is inspired from the [bin-v8-flags-filter](https://www.npmjs.com/package/bin-v8-flags-filter) package in npm.

This version spawns the child process synchronously whereas the bin-v8-flags-filter spawns the process asynchronously.

# bin-v8-flags-filter-sync


*Filters out v8 flags for your Node.js CLIs.*

Filters out well-known v8 flags given to your app and spawns new process synchronously with v8 flags passed to Node.js and the rest
of the args passed to your actual CLI. Basically an extraction of related [mocha code](https://github.com/mochajs/mocha/blob/master/bin/mocha).

## Install
```
npm install bin-v8-flags-filter-sync
```

## Usage
*In JS file specified as `bin` in your `package.json`:*
```js
const v8FlagsFilter = require('bin-v8-flags-filter-sync');
const path = require('path');

const cliPath = path.join(__dirname, './cli.js'); // Path to your actual CLI file that contains app code.

v8FlagsFilter(cliPath);
```

### API
#### `v8FlagsFilter(path, [options])`
 - `path` - path to CLI script.
 - `options` - an optional object with the following optional keys:
   - `ignore` - an array of v8 flags to ignore, i.e. to _not_ filter-out when spawning a new process.
   - `forcedKillDelay` - a number of milliseconds after which to send a kill command to the spawned process, only after an interrupt has already been issued.  Defaults to `30000`.
   - `useShutdownMessage` - rather than forwarding along interrupt signals to the spawned process, instead forwards a `'shutdown'` message to the spawned process.

## Author
[Vinay Vennela](https://github.com/vinayvennela) (v.vinay317@gmail.com)