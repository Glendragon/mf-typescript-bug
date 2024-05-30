# @module-federation/typescript Upgrade Issue

Upgrading `@module-federation/typescript` from v3.1.1 to v3.1.2 breaks with npm.

## Environment

- **npm**: 10.8.1
- **node**: 20.12.2

## Steps to Reproduce

1. Create a new directory and navigate into it:
    ```sh
    mkdir webpack-demo
    cd webpack-demo
    ```

2. Initialize a new npm project:
    ```sh
    npm init -y
    ```

3. Install the required packages:
    ```sh
    npm install webpack webpack-cli @module-federation/typescript --save-dev
    ```

4. Append the following line to `webpack.config.js`:
    ```sh
    echo "const { FederatedTypesPlugin } = require('@module-federation/typescript');" >> webpack.config.js
    ```

5. Run the webpack build:
    ```sh
    npx webpack build
    ```

## Error

```plaintext
[webpack-cli] Failed to load 'webpack-demo/webpack.config.js' config
[webpack-cli] Error: Cannot find module 'axios'
Require stack:
- webpack-demo/node_modules/@module-federation/typescript/dist/src/plugins/FederatedTypesPlugin.js
- webpack-demo/node_modules/@module-federation/typescript/dist/src/index.js
- webpack-demo/webpack.config.js
- webpack-demo/node_modules/webpack-cli/lib/webpack-cli.js
- webpack-demo/node_modules/webpack-cli/lib/bootstrap.js
- webpack-demo/node_modules/webpack-cli/bin/cli.js
- webpack-demo/node_modules/webpack/bin/webpack.js
    at Module._resolveFilename (node:internal/modules/cjs/loader:1143:15)
    at Module._load (node:internal/modules/cjs/loader:984:27)
    at Module.require (node:internal/modules/cjs/loader:1231:19)
    at require (node:internal/modules/helpers:179:18)
    at Object.<anonymous> (webpack-demo/node_modules/@module-federation/typescript/dist/src/plugins/FederatedTypesPlugin.js:9:33)
    at Module._compile (node:internal/modules/cjs/loader:1369:14)
    at Module._extensions..js (node:internal/modules/cjs/loader:1427:10)
    at Module.load (node:internal/modules/cjs/loader:1206:32)
    at Module._load (node:internal/modules/cjs/loader:1022:12)
    at Module.require (node:internal/modules/cjs/loader:1231:19) {
  code: 'MODULE_NOT_FOUND',
  requireStack: [
    'webpack-demo/node_modules/@module-federation/typescript/dist/src/plugins/FederatedTypesPlugin.js',
    'webpack-demo/node_modules/@module-federation/typescript/dist/src/index.js',
    'webpack-demo/webpack.config.js',
    'webpack-demo/node_modules/webpack-cli/lib/webpack-cli.js',
    'webpack-demo/node_modules/webpack-cli/lib/bootstrap.js',
    'webpack-demo/node_modules/webpack-cli/bin/cli.js',
    'webpack-demo/node_modules/webpack/bin/webpack.js'
  ]
}
```
