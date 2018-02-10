# Webpack


## Version

^Webpack 2

## My basic webpack config

This is an example of webpack config file I copy from my **React** project. I use [ant design](https://ant.design) as my UI library.

```js
const webpack = require('webpack');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const ExtractTextPlugin = require('extract-text-webpack-plugin');
const path = require('path');
const fs  = require('fs');

const APP_INDEX = path.join(__dirname, "/index.js");
const APP_DIR = path.join(__dirname, "/");
const BUILD_PATH = path.join(__dirname, "/dist");
const publicPath = path.join(__dirname, '/public');

module.exports = {
    entry: APP_INDEX,
    output: {
        filename: '[name].js', //output name after building
        path: BUILD_PATH,
        chunkFilename: '[name].min.js',
        publicPath: '/'
    },

    resolve: {
        extensions: [".js", ".json"],
        alias: {
            // with alias you can simply use like: 
            // import Something from '@Components/Something'
            '@Components': path.resolve(__dirname, 'components/'),
        }
    },

    // Enable sourcemaps for debugging webpack's output.
    devtool: "source-map",

    module: {
        rules: [
            {
                test: /\.(js|jsx)$/,
                loader: 'babel-loader',
                include: [
                    APP_DIR
                ],
                exclude: /node_modules/
            },
            {
                test: /\.css$/,
                loader: ExtractTextPlugin.extract({ fallback: 'style-loader', use: 'css-loader' }),
                exclude: /node_modules/,
            },
            {
                test: /.less$/,
                include: [
                    // include ant design
                    path.resolve(__dirname, 'node_modules/antd'),
                    APP_DIR
                ],
                use: ExtractTextPlugin.extract({
                  fallback: 'style-loader',
                  use: [{
                      loader: 'css-loader',
                    },
                    {
                      loader: 'less-loader',
                      options: {
                        sourceMap: true,
                        modules: false,
                        modifyVars: theme,
                      },
                    },
                  ],
                }),
            },
            {
                test: /\.scss$/,
                loader: ExtractTextPlugin.extract({ fallback: 'style-loader', use: 'sass-loader' }),
                exclude: /node_modules/,
            },
            {
                test: /\.(eot|woff|svg|ttf|woff2|gif|appcache)(\?|$)/,
                exclude: /node_modules/,
                loader: 'file-loader?name=[name].[ext]'
            },
            {
                test: /\.(png|jpg|jpeg|gif)$/,
                exclude: /node_modules/,
                // while the image file is small than the value of limit, it will be encoded in base64
                loader: 'url-loader?limit=8192', //url-loader?limit=8192&name=images/[name].[ext]
            }
        ]
    },
    plugins: [
        new HtmlWebpackPlugin({
            title: productConfig.title,
            desc: productConfig.description,
            content: productConfig.content,
            template: path.join(__dirname, "/template/index.template.html"),
            react_cdn: "https://unpkg.com/react@16/umd/react.development.min.js",
            react_dom_cdn: "https://unpkg.com/react-dom@16/umd/react-dom.development.min.js"
        }),
        new webpack.DefinePlugin({
            "process.env": {
                //define node environment
                NODE_ENV: JSON.stringify('development'),
                // define anny process env here, and can be accessed as
                // process.env.STH
            }
        }),
        new ExtractTextPlugin("[name]-[hash].css"),
        // use following two plugins for production
        new webpack.optimize.CommonsChunkPlugin({ name: 'vendor', filename: 'vendor.bundle.js' }),
        new webpack.optimize.UglifyJsPlugin({
            output: {
                // remove all comments
                comments: false,
            },
            compress: {
                warnings: false,
                 // Drop console statements
                drop_console: true
            }
        })
    ],

    // When importing a module whose path matches one of the following, just assume
    // a corresponding global variable exists and use that instead. This is
    // important because it allows us to avoid bundling all of our dependencies,
    // which allows browsers to cache those libraries between builds.
    externals: {
        "react": "React", "react-dom": "ReactDOM"
    }
};
```

## Some usefull scripts in package.json

Usually I have two webpack config file, one is for developing **webpack.config.dev.js**, another one for production **webpack.config.prod.js**

```json
"scripts": {
    "dev": "webpack-dev-server --config webpack.config.dev.js",
    "prod": "webpack --config webpack.config.prod.js",
}
```