# 配置webpack

## 全局安装webpack

使用npm全局安装

```
npm install webpack -g
```

创建一个测试项目

```
npm init
```

安装webpack到开发依赖

```
npm install webpack --save-dev
```

安装完成后我们写一个hello world的测试项目：

首先在根目录创建**webpack.config.js** 并在 build目录下创建**app.js** 并随便写点什么 。

```js
var webpack = require('webpack');

module.exports = {
  entry: './build/app.js', //入口文件
  output: {
    path: './src/javascripts/', //输出目录
    filename: 'app.min.js', //输出文件名
    publicPath: './src/javascripts/' //文件中引用的输出文件链接地址
  },
  plugins: [
    new webpack.DefinePlugin({
      'process.env': {
        'NODE_ENV': '"development"' //开发环境设置为development
      }
    })
  ]
}
```



