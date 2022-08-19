# Flow React Relay Demo

## Steps to reproduce:
1) Run `yarn` to install dependencies
2) Run `yarn flow`, which shows an error with the following import:
```
Error ┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈┈ src/index.js:3:8

Importing from an untyped module makes it any and is not safe! Did you mean to add // @flow to the top of
react-relay/lib/relay-hooks/ProfilerContext? [untyped-import]

     1│ // @flow strict-local
     2│
     3│ import ProfilerContextActual from 'react-relay/lib/relay-hooks/ProfilerContext';
     4│ import ProfilerContextDefs from 'react-relay/relay-hooks/ProfilerContext';
     5│
     6│ console.log({
```
3) Run `yarn build` to compile the code with babel
4) Run `yarn start` to run the built file with node, and you will see an error similar to the following:
```
$ node dist/index.js
node:internal/modules/cjs/loader:936
  throw err;
  ^

Error: Cannot find module 'react-relay/relay-hooks/ProfilerContext'
Require stack:
- ~/flow-react-relay/dist/index.js
    at Function.Module._resolveFilename (node:internal/modules/cjs/loader:933:15)
    at Function.Module._load (node:internal/modules/cjs/loader:778:27)
    at Module.require (node:internal/modules/cjs/loader:1005:19)
    at require (node:internal/modules/cjs/helpers:102:18)
    at Object.<anonymous> (~/flow-react-relay/dist/index.js:5:48)
    at Module._compile (node:internal/modules/cjs/loader:1105:14)
    at Object.Module._extensions..js (node:internal/modules/cjs/loader:1159:10)
    at Module.load (node:internal/modules/cjs/loader:981:32)
    at Function.Module._load (node:internal/modules/cjs/loader:822:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:77:12) {
  code: 'MODULE_NOT_FOUND',
  requireStack: [ '~/flow-react-relay/dist/index.js' ]
}
error Command failed with exit code 1.
```