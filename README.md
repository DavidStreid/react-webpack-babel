# Webpack-Babel configurations w/ React
Setup for using webpack and babel w/ React.

Webpack is configured via './webpack.config.js'. It uses the 'babel-loader' to transpile ES6, which is configured by '.babelrc'.

The webpack/babel dependencies are all the modules in the 'devDependencies' field of the './package.json'

## Mandatory Changes for setup
.babel.rc
```
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

webpack.config.js
```
const path = require('path');

module.exports = {
    entry: './src/index.js',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js'
    },
    module: {
        rules: [
            {
                test: /\.(js|jsx)$/,
                exclude: /node_modules/,
                use: {
                    loader: "babel-loader"
                }
            },
            {
                test: /\.css$/i,
                use: ['style-loader', 'css-loader'],
            }
        ]
    }
};
```

## Development
```
$ npm run wstart 
```

## Build
```
$ npm run wbuild 
```