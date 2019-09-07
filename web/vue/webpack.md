[TOC]

## 在网页中会引用哪些常见的资源

* JS
  * .js    .jsx    .coffee    .ts（TypeScript）
* CSS
  * .css    .less    .sass    .scss
* Images
  * .jpg    .gif     .png    .bmp    .svg
* 字体文件（Fonts）
  * .svg    .ttf     .ect    .woff    .woff2
* 模板文件
  * .ejs    .jade    .vue

## 网页中引入的表态资源多了以后有什么问题

1. 网页加载速度慢，因为，我们要发起很多的二次请求
2. 要处理错综复杂的依赖关系

## 如何解决上述两个问题

1. 合并、压缩、精灵图、图片的 Base64 编码（适用于小图片）
2. 可以使用 requireJS、也可以使用 webpack 解决各个包之间复杂的依赖关系

## 什么是 Webpack

一个前端的项目构建工具，它是基于 Node.js 开发出来的一个前端工具

## 如果完美实现上述的 2 种解决方案

1. 使用 Gulp，是基于 task 任务的
2. 使用 Webpack，是基于整个项目进行构建的

* 借助于 webpack 这个前端自动化构建工具，可以完美实现资源的合并、打包、压缩、混淆等诸多功能
* [官网](https://webpack.js.org/)

## webpack 安装的 2 种方式

1. 运行 `sudo npm i webpack -g` 全局安装 webpack，这样就能在全局使用 webpack 的命令
2. 在项目根目录中运行 `npm i webpack --save-dev` 安装到项目依赖中

> 后面需要用到 cli，所以还得在全局和在项目中安装 cli，否则不能使用 webpack 命令

## 实现 webpack 的实时打包构建

1. 由于每次重新修改代码之后，都需要重新输入 webpack 打包构建的命令，非常麻烦，因此使用 `webpack-dev-server` 实现代码实时打包编译，当修改代码之后，会自动进行打包构建
2. 运行 `cnpm i webpack-dev-server --save-dev` 安装到开发依赖
3. 安装完成后，在命令行直接运行 `webpack-dev-server` 进行打包，发现报错，此时需要借助于 `package.json` 文件中的指令，来运行 `webpack-dev-server` 命令，在 `scripts` 节点下新增 `"dev": "webpack-dev-server` 指令，发现可以进行实时打包，但是 dist 目录下并没有生成 `bundle.js` 文件，这是因为 `webpack-dev-server` 将打好的包放在了内存中

* 把 `bundle.js` 放在内存中的好处是：由于需要实时打包编译，所以放在内存中速度会非常快
* 这个时候访问 `webpack-dev-server` 启动的 `http://localhost:8080` 网站，发现是一个文件夹的面板，需要点击到 `src` 目录下，才能打开我们的 index 首页，此时引用不到 bundle.js 文件，需要修改 index.html 中 srcipt 的 src 属性为：`<script src="../bundle.js"></script>`
* 为了能在访问 `http://localhost:8080` 的时候直接访问 index.html 页面，可以使用 `--contentBase src` 指令来修改 dev 指令，指定启动的根目录：`"dev": "webpack-dev-server --contentBase src`，同时修改 index 页面中 script 的 src 属性为 `<script src="bundle.js"></script>`

## 使用 html-webpack-plugin 插件配置启动页面

由于使用 `--contentBase` 指令的过程比较繁琐，需要指定启动的目录，同时还需要修改 index.html 中 script 标签的 src 属性，所以推荐大家使用 `html-webpack-plugin` 插件配置启动页面。

1. 运行 `cnpm i html-webpack-plugin --save-dev` 安装到开发依赖

2. 修改 `package.config.js` 配置文件如下：

   ```javascript
   // 导入路径的模块
   var path = require('path')
   // 导入自动生成的 HTML 文件的插件
   var htmlWebpackPlugin = require('html-webpack-plugin')
   
   module.export = {
     entry: path.resolve(__dirname, 'src/js/main.js'), // 项目入口文件
     output: { // 配置输出选项
       path: path.resolve(__dirname, 'dist'), //配置输出的路径
       filename: 'bundle.js' //配置输出的文件名
     },
     plugins: [ // 配置 plugins 节点配置插件
       new htmlWebpackPlugin({
         template: path.resolve(__dirname, 'src/index.html'), //模板路径
         filename: 'index.html' // 自动生成的 HTML 文件的名称
       })
     ]
   }
   ```

3. 修改 `package.json` 中 `script` 节点中的 dev 指令如下：

   `"dev": "webpack-dev-server"`

4. 将 index.html 中 script 标签注释掉，因为 `html-webpack-plugin` 插件自动把 bundle.js 注入到 index.html 页面中

## 在普通页面中使用 render 函数渲染组件

