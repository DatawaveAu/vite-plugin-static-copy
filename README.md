# vite-plugin-static-copy

[![npm version](https://badge.fury.io/js/vite-plugin-static-copy.svg)](https://badge.fury.io/js/vite-plugin-static-copy) ![CI](https://github.com/sapphi-red/vite-plugin-static-copy/workflows/CI/badge.svg) ![automatic deploy](https://github.com/sapphi-red/vite-plugin-static-copy/workflows/automatic%20deploy/badge.svg) [![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)  

`rollup-plugin-copy` for vite with dev server support.

## Install
```shell
npm i -D vite-plugin-static-copy # yarn add -D vite-plugin-static-copy
```

## Usage
Add `viteStaticCopy` plugin to `vite.config.js` / `vite.config.ts`.
```js
// vite.config.js / vite.config.ts
import { viteStaticCopy } from 'vite-plugin-static-copy'

export default {
  plugins: [
    viteStaticCopy({
      targets: [
        {
          src: 'bin/example.wasm',
          dest: 'wasm-files'
        }
      ]
    })
  ]
}
```

For example, if you use the config above, you will be able to fetch `bin/example.wasm` with `fetch('/wasm-files/example.wasm')`.

### Options
See [options.ts](https://github.com/sapphi-red/vite-plugin-static-copy/blob/main/src/options.ts).

## Differences with `rollup-plugin-copy`
- `dest` is limited inside [`build.outDir`](https://vitejs.dev/config/#build-outdir).
- [`fast-glob`](https://www.npmjs.com/package/fast-glob) is used instead of [`globby`](https://www.npmjs.com/package/globby).
  - Because `fast-glob` is used inside `vite`.
