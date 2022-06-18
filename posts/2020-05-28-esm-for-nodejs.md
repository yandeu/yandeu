# ECMAScript modules for Node.js

I decided to completely drop CommonJS from January 2022.

## What will change?

All my modules will only support Node.js v14 and v16 beginning from January 2022.

New Packages will only support Node.js v14 and v16 from the start.

## How do I do it?

Like so:

```json
// package.json
{
  "type": "module",
  "engines": {
    "node": "^14.15 || >=16"
  }
}
```

```js
// .npmrc
engine-strict=true
```

```json
// tsconfig.json
{
  "compilerOptions": {
    "target": "ES2020",
    "module": "es2020",
    "moduleResolution": "node",

    "rootDir": "src",
    "outDir": "dist",

    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "newLine": "lf"
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "**/*.spec.ts"]
}
```
## Replace dirname and filename

```js
import { dirname } from 'path'
import { fileURLToPath } from 'url'
const __filename = fileURLToPath(import.meta.url)
const __dirname = dirname(__filename)
```

## Include ES Modules into a CommonJS codebase?

Yes, it is possible using [`Dynamic Imports`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import#dynamic_imports).

Example:

```js
// index.cjs

const main = async () => {
  const esmPackage = await import('esm-package')
  // or maybe
  const { module } = await import('esm-package')

  // now use the esm-package like you are used to
}

main()
```

## Badge

I will probably add the badge below to ESModule-Only packages:

[![ES Modules Badge](https://img.shields.io/badge/Node.js-ES%20Modules-informational?style=flat-square)](https://github.com/yandeu/yandeu/blob/main/posts/2020-05-28-esm-for-nodejs.md) / [![ES Modules Badge](https://img.shields.io/badge/Node.js-ES%20Modules-informational)](https://github.com/yandeu/yandeu/blob/main/posts/2020-05-28-esm-for-nodejs.md)
