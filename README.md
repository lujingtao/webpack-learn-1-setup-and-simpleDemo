
# 一、webpack是什么
官方定义：本质上，webpack 是一个现代 JavaScript 应用程序的静态模块打包器(module bundler)。当 webpack 处理应用程序时，它会递归地构建一个依赖关系图(dependency graph)，其中包含应用程序需要的每个模块，然后将所有这些模块打包成一个或多个 bundle。

# 二、webpack能干什么
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190829103414516.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2lhbWx1amluZ3Rhbw==,size_16,color_FFFFFF,t_70)
上面的概念看起来比较懵，在实际应用中，其实它就是帮你处理文件依赖关系（js、css、图片），把你在开发环境中用到的sass、less、es6、typescript等浏览器不能识别的代码转换为我们常用的js、css等，并且它是模块化管理，按需加载的。

再概况说明就是提供了一个工作环境，该环境能自动化处理项目中需要用到的各种功能（js、css、图片压缩，sass、less转换为css，es6、typescript转换为js等），让开发人员只需专注业务处理。

# 三、webpack安装
webpack是基于nodejs的，所以要先安装nodejs，安装方法请自行百度。
现在我们开始一个示例，来正式进入webpack的使用。

## 1、我们先建立一个项目文件夹\webpackDemo
## 2、初始化npm
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190829103438407.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2lhbWx1amluZ3Rhbw==,size_16,color_FFFFFF,t_70)
这里我们在vsCode上示范，左侧打开webpackDemo文件夹，再新建一个终端

    输入 npm init -y

ps：建议先安装cnpm，使用国内的服务安装，npm默认是国外服务器，经常抽风。cnpm安装和使用方法请自行百度。

执行成功后会发现文件夹下多了一个 package.json，这是npm用于管理依赖包的，你可以根据需要修改。
## 3、安装webpack
    输入 npm install --save-dev webpack

ps：默认是本地安装，如需全局安装，则增加-g，建议本地安装
## 4、安装webpack-cli （webpack命令行界面，安装了才可以执行wepack命令）

    输入 npm install --save-dev webpack-cli

直至目前，安装和准备工作已做好，现在开始正式使用webpack

# 四、webpack使用
我们先实现最简单demo来直观提现webpack的打包功能。
## 1、先建立我们实际工作用到的文件，dist用于存放打包后的文件，src用于存放是开发环境时的代码
/dist/index.html
/src/index.js

index.html代码：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>webpack test</title>
  </head>
  <body>
    <script src="bundle.js"></script>
  </body>
</html>
```

index.js代码：

```js
let ele = document.createElement('h1');
ele.innerHTML = "Hello 大话主席!";
document.body.appendChild(ele);
```

## 2、配置webpack.config.js（wepack配置文件，用于设定入口文件、打包路径、插件加载等，wepack核心文件）
建立 /webpack.config.js，并编写代码：

```js
module.exports = {
  entry:  __dirname + "/src/index.js",//唯一入口文件
  output: {
    path: __dirname + "/dist",//打包后的文件存放的地方
    filename: "bundle.js"//打包后输出文件的文件名
  }
}
```

## 3、执行webpack

    输入 npx webpack

执行后发现 dist下多了 bundle.js 文件，此时浏览器打开index.html，发现执行后代码效果。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190829103725350.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2lhbWx1amluZ3Rhbw==,size_16,color_FFFFFF,t_70)
有兴趣可以看看 bundle.js 源码。

目前为止，我们的项目文档结构如下
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190829103813968.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2lhbWx1amluZ3Rhbw==,size_16,color_FFFFFF,t_70)

至此，我们使用webpack实现了最简单的demo，下篇我们将介绍webpack更多功能。

