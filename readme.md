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
    ...
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
