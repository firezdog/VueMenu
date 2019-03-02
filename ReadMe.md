# Setup

https://itnext.io/vuejs-and-webpack-4-from-scratch-part-1-94c9c28a534a

npm install --save vue vue-router\
npm install --save-dev webpack webpack-cli

./src
* components -- building blocks
* pages -- top level Vue components
* router -- Vue router
* app.js -- entrypoint
* App.vue -- root component

## Webpack

Bundle dependencies. Loaders handle different file-types (e.g. CSS). See webpack.config.dev.js.

"test" property specifies the file-type to use with a loader (regex).

exclude node_modules for faster compiling

### For Vue:
npm install --save-dev vue-loader vue-template-compiler vue-style-loader css-loader

in package.json:\
"build": "webpack --config build/webpack.config.dev.js

.html in root to load bundle (as dist/main.js).

### To automatically rebuild on change
npm install --save-dev webpack-dev-server\
"dev": "webpack-dev-server --config build/webpack.config.dev.js"

npm install --save-dev html-webpack-plugin
Remove script to dist/main.js in index.html
add to webpack config

Add config keep page from being refreshed (under "devServer")

### Styling