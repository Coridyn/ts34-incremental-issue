# TypeScript 3.4 RC incremental build path issue

## To reproduce failing build

Clone project, `npm install`, then run:

```
$ npm run buildFail
```


## Issue description

Build fails when `rootDir` is passed as CLI flag:

 * `"incremental": true`
 * `outDir` has value (doesn't matter if the value is from `tsconfig.json` or CLI)
 * `--rootDir <my path>` **set from CLI**

Fails with this error:

```bash
Error: Debug Failure. False expression: Paths must either both be absolute or both be relative
    at Object.getRelativePathFromDirectory (C:\\projects\\node_modules\\typescript\\lib\\tsc.js:12393:15)
    at Object.getOutputPathForBuildInfo (C:\\projects\\node_modules\\typescript\\lib\\tsc.js:67425:55)
    at Object.readBuilderProgram (C:\\projects\\node_modules\\typescript\\lib\\tsc.js:76379:32)
    at performIncrementalCompilation (C:\\projects\\node_modules\\typescript\\lib\\tsc.js:78142:29)
    at Object.executeCommandLine (C:\\projects\\node_modules\\typescript\\lib\\tsc.js:78042:17)
    at Object.<anonymous> (C:\\projects\\node_modules\\typescript\\lib\\tsc.js:78285:4)
    at Module._compile (internal/modules/cjs/loader.js:721:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:732:10)
    at Module.load (internal/modules/cjs/loader.js:620:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:560:12)
```


## Working build

Build works when `rootDir` is set in `tsconfig.json`:
 * `"incremental": true`
 * `outDir` has value
 * `"rootDir": "<my path>"` set from `tsconfig.json`

```
$ npm run buildWork
```


## Environment information

OS: Windows 10 1809 (17763.379)
nodejs version: v11.6.0
npm version: 5.3.0
typescript version: typescript@3.4.0-dev.20190316
