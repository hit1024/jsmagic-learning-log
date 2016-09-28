* 乱糟糟的代码不可为，模块化乃天数。
* CommonJS 是一种模块化规范，使用 require() 导入（并得到返回值），module.exports 导出，default 是默认导出。
* babel 转换时，会给模块加上一些代码做兼容：给模块加 __esModule 属性标志它是 ES6 模块
* Webpack 是一个复杂的打包工具


参考文献：

* [Webpack 中文指南——CommonJS 规范](http://zhaoda.net/webpack-handbook/commonjs.html)
