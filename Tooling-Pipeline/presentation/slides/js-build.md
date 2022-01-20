# JS Build


## Babel
Transform JavaScript to standard ES5/6.


## Webpack
Bundle multiple JavaScript files together to create a web compatible build artifact.


## webpack.config.js
```
const path = require('path');

module.exports = {
  entry: './src/index.ts',
  module: {
    rules: [
      {
        test: /\.tsx?$/,
        use: 'ts-loader',
        exclude: /node_modules/,
      },
    ],
  },
  resolve: {
    extensions: ['.tsx', '.ts', '.js'],
  },
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```


## Requirements

Your project should have at least 2 TS files that are combined into 1 file that will be served via the browser.
