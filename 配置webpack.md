# 配置webpack

## 安装webpack并测试

使用npm全局安装

```
npm install webpack -g
```

创建一个测试项目

```
npm init
```

在package.json中添加webpack并安装webpack到开发依赖。（vue-loader使用2.0以上的webpack才能正常编译）

```
"webpack": "^2.1.0-beta.25"
```

你也可以使用`vue-cli`进行安装配置，详见[NPM说明](https://www.npmjs.com/package/vue-loader)。

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

在src目录中创建index.html文件，并引入输出的javascript文件

```
<!doctype html>
<head>
    <meta charset="utf-8" />
    <title>Vue in-page app test</title>
</head>
<body>
    <div id="app">
        <div id="render"></div>
    </div>
    <script src="./javascripts/app.min.js"></script>
</body>
</html>
```

在命令行中使用webpack命令打包（添加-p可压缩）项目文件。此时访问index.html即可看到app.js中执行的内容了。

