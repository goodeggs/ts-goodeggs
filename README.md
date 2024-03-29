# Typescript things for Good Eggs

> Typescript, TSLint, and Prettier configs

_❌ This library is deprecated. Do not use it in new code and strive to remove it from existing code. See https://github.com/goodeggs/goodeggs-toolkit and https://github.com/goodeggs/goodeggs-tsconfig instead. ❌_

## Installation

```sh
yarn add --dev tslint typescript-tslint-plugin prettier ts-goodeggs
```

## Usage

In `tsconfig.json`:

For an application:

```json
{
  "extends": "ts-goodeggs/tsconfig",
  "compilerOptions": {
    "outDir": "build"
  },
  "include": [
    "src"
  ]
}
```

For a module:

```json
{
  "extends": "ts-goodeggs/tsconfig",
  "compilerOptions": {
    "outDir": "build"
  },
  "exclude": ["node_modules", "build"]
}
```

In `tslint.json`:

```json
{
  "extends": "ts-goodeggs/tslint"
}
```

In `prettier.config.js`:

```js
//tslint:disable
module.exports = require('ts-goodeggs/prettier');
```

In `package.json`:

```json
{
  "scripts": {
    "build": "yarn run build:ts",
    "build:ts": "ts-goodeggs build",
    "clean": "rm -rf build",
    "distclean": "yarn run clean && rm -rf node_modules",
    "lint": "yarn run lint:ts && yarn run lint:docs",
    "lint:ts": "ts-goodeggs lint",
    "lint:docs": "yarn run lint:docs:glob '**/*.{yml,json,md}'",
    "lint:docs:glob": "prettier --ignore-path .gitignore --list-different",
    "fmt": "yarn run fmt:ts && yarn run fmt:docs",
    "fmt:ts": "ts-goodeggs fmt",
    "fmt:docs": "yarn run fmt:docs:glob '**/*.{yml,json,md}'",
    "fmt:docs:glob": "prettier --ignore-path .gitignore --write"
  }
}
```
