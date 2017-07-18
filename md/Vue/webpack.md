# webpack

* webpack可以看做是模块打包机:用于分析项目结构,找到JavaScript模块以及其它的一些浏览器不能直接运行的拓展语言(Scss,TypeScript等),并将其打包为合适的格式以供浏览器使用
* webpack的工作方式: 把项目当做一个整体,通过一个给定的主文件(如:index.js),webpack将从这个文件开始找到你的项目的所有依赖文件,使用loaders处理它们,最后打包为一个浏览器可识别的JavaScript文件
* webpack参考网站: http://www.jianshu.com/p/42e11515c10f

# webpack安装配置

* 安装webpack

```
//全局安装
npm install -g webpack
//安装到你的项目目录(需要在安装目录中运行命令行)
npm install --save-dev webpack
```

* 在创建好的项目文件夹中创建一个package.json文件,这是一个标准的npm说明文件,里面包括当前项目的依赖模块,自定义的脚本任务等等,在命令行运行"npm init""命令后,命令行会让你输入项目名称,项目描述,作者等信息等等,不如果你不准备在npm中发布你的模块,这些问题可以跳过,回车默认即可
* 安装sass less webpack,一般采用的都是本地安装而不是全局安装,因为在开发的时候不可能所有人电脑中的版本都是一样的,这样就会导致兼容问题,本地安装可以解决这个问题
* webpack中文网站: http://www.css88.com/doc/webpack2/concepts/
* --save-dev: 开发的时候依赖的模块(webpack gulp less less-loader)
* --save: 上线发布后依然需要的模块(vue react jQuery BootStrap....)
* 创建配置文件: 
    * npm init -y
    * npm install webpack webpack-dev-server --save-dev
* 安装vue相关:
    * npm install vue-loader vue-template-compiler --save-dev
    * npm install vue vue-router --save
* 相关解析模块:
    * css解析模块: npm install css-loader style-loader --save-dev
    * less解析模块: npm install less less-loader --save-dev
    * 图片解析模块: npm install file-loader url-loader --save-dev
# 使用webpack构建本地服务器

*  webpack可以建立本地服务,让浏览器监测代码并自动刷新修改后的结果,这需要一个单独的模块支持,下载模块: npm install webpack-dev-server --save-dev 

# Bable

* Bable是一个编译JavaScript代码的平台,例如可以将ES6,ES7语法转译为ES5语法
* Babel其实是几个模块化的包,其核心功能位于称为babel-core的npm包中,不过webpack把它们整合在一起使用,但是对于每一个你需要的功能或拓展,都需要安装单独的包
* Bable核心包: npm install babel-core babel-loader --save-dev
* ES6语法转译: npm install babel-preset-es2015 --save-dev
* ES7语法转译: npm install babel-preset-stage-0 --save-dev