# ui5-shim-babel-polyfill
Custom UI5 project shim extension for babel polyfill dependencies.

As of Babel 7.4.0, [@babel/polyfill](https://babeljs.io/docs/en/babel-polyfill) has been deprecated in favor of directly including [core-js/stable](https://github.com/zloirock/core-js) (to polyfill ECMAScript features) and [regenerator-runtime/runtime](https://github.com/facebook/regenerator/tree/master/packages/regenerator-runtime) (needed to use transpiled generator functions).

Using this project shim both dependencies can be easily consumed in your ui5 application.

This is especially useful when using [ui5-task-babel](https://github.com/pwasem/ui5-task-babel) or [ui5-middleware-babel](https://github.com/pwasem/ui5-middleware-babel).

## Prerequisites
Make sure your project is using the latest [UI5 Tooling](https://sap.github.io/ui5-tooling/pages/GettingStarted/).

## Getting started

### Install

#### Custom project shim
Add the custom project shim and its peer dependencies as `dependencies` to your project.

With `yarn`:
```sh
yarn add ui5-shim-babel-polyfill core-js-bundle regenerator-runtime
```
Or `npm`:
```sh
npm i ui5-shim-babel-polyfill core-js-bundle regenerator-runtime
```

Additionally the custom project shim its peer dependencies need to be manually defined in `ui5.dependencies` in your project's `package.json`:
```json
{
  "ui5": {
    "dependencies": [
      "ui5-shim-babel-polyfill",
      "core-js-bundle",
      "regenerator-runtime"
    ]
  }
}
```

### Usage
Register [core-js/stable](https://github.com/zloirock/core-js) and [regenerator-runtime/runtime](https://github.com/facebook/regenerator/tree/master/packages/regenerator-runtime) as resources your projects `manifest.json`.

This will ensure both dependencies will be included once in your app and all required polyfills will be available for your transpiled code.
```json
{
  "sap.ui5": {
    "resources": {
      "js": [
        {
          "uri": "/resources/core-js-bundle/minified.js"
        },
        {
          "uri": "/resources/regenerator-runtime/runtime.js"
        }
      ]
    }
  }
}
```
