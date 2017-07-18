# vue-cli

* 一个能够自动生成Vue项目的插件
* 使用这个插件的前提是必须有webpack插件
* 安装插件,在全局环境中安装: npm install vue-cli -g:
* vue init simple 项目名: 能够自动生成一个新的vue项目(基本不用)
* vue init webpack-simple 项目名: 生成vue项目模板

# 生成Vue项目的流程

```
$ vue init webpack exprice --------------------- 这个是那个安装vue脚手架的命令
This will install Vue 2.x version of the template. ---------------------这里说明将要创建一个vue 2.x版本的项目
For Vue 1.x use: vue init webpack#1.0 exprice
? Project name (exprice) ---------------------项目名称
? Project name exprice
? Project description (A Vue.js project) ---------------------项目描述
? Project description A Vue.js project
? Author Datura --------------------- 项目创建者
? Author Datura
? Vue build (Use arrow keys)
? Vue build standalone
? Install vue-router? (Y/n) --------------------- 是否安装Vue路由，也就是以后是spa（但页面应用需要的模块）
? Install vue-router? Yes
? Use ESLint to lint your code? (Y/n) n ---------------------是否启用eslint检测规则，这里个人建议选no
? Use ESLint to lint your code? No
? Setup unit tests with Karma + Mocha? (Y/n)
? Setup unit tests with Karma + Mocha? Yes
? Setup e2e tests with Nightwatch? (Y/n)
? Setup e2e tests with Nightwatch? Yes
vue-cli · Generated "exprice".
To get started: --------------------- 这里说明如何启动这个服务
cd exprice
npm install
npm run dev
```
* 安装项目依赖:npm install,因为自动构建过程中已存在package.json文件,所以这里直接安装依赖就行,不要从国内镜像cnpm安装(会导致后面缺了很多依赖库)
* 除了安装项目依赖之外还需要安装vue路由模块(vue-router)和网络请求模块(vue-resource): npm install vue-router vue-resource --save
* 启动项目: npm run dev
* 注意: 项目启动的时候默认使用的是8080端口,在启动之前要确保没有占用这个端口
* 如果当前vue-cli版本过低可能会报错,需要更新vue-cli: npm update vue-cli
* 查看当前vue-cli版本: npm view vue-cli
* 基本使用方法参考文档: http://www.runoob.com/w3cnote/vue2-start-coding.html

# 项目文件夹详解

* 根目录
    * build -------------- 构建脚本目录
    * config ------------- 构建配置目录
    * node_modules ------- 依赖的node工具包目录
    * src ---------------- 源码目录
        * assect --------- 资源目录
        * components ----- 组件目录
        * router --------- 路由相关组件目录
            * App.vue ---- 页面级Vue组件
            * main.js ---- 页面入口JS文件
    * static ------------- 静态文件目录
    * test --------------- 测试文件目录
        * .babelrc
        * .editorconfig
        * .eslintignore
        * .eslintrc.js --- ES语法检测配置
        * .gitignore
        * index.html ----- 项目主页
        * package.json --- 项目描述文件
        * README.md