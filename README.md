# vis.js

[![Join the chat at https://gitter.im/vis-js/Lobby](https://badges.gitter.im/vis-js/Lobby.svg)](https://gitter.im/vis-js/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

<a href="https://github.com/almende/vis/blob/develop/misc/we_need_help.md">
  <img align="right" src="https://13581803628.github.io/img/we_need_help.jpg">
</a>

Vis.js 一个动态的基于浏览器的可视化库。
这个库设计原则是使用简单、处理大量动态数据并对其进行操作运算。
该库由以下组件组成：

- DataSet 和 DataView. 一个基于数据集的灵活的键值对。
  添加、更新、删除数据项。
  定制数据集修改方法。
  一个 DataSet 可以对数据项进行过滤和排序，也可以变换数据项的字段。
- DataView. 一个已过滤和/或格式化的DataSet视图。
- Graph2d. 用线或直方图在时间轴上绘制数据。
- Graph3d. 用三维图表可视化数据。
- Network. 使用节点和边展示一个网络图（强制为有向图）。
- Timeline. 在时间轴上显示不同类型的数据。

这个 vis.js 库最初是由 [Almende B.V](http://almende.com) 开发的。

## 徽章

[![NPM](https://nodei.co/npm/vis.png?downloads=true&downloadRank=true)](https://nodei.co/npm/vis/)

[![Dependency Status](https://david-dm.org/almende/vis/status.svg)](https://david-dm.org/almende/vis)
[![devDependency Status](https://david-dm.org/almende/vis/dev-status.svg)](https://david-dm.org/almende/vis?type=dev)

[![last version on CDNJS](https://img.shields.io/cdnjs/v/vis.svg)](https://cdnjs.com/libraries/vis)
[![GitHub contributors](https://img.shields.io/github/contributors/almende/vis.svg)](https://github.com/almende/vis/graphs/contributors)
[![GitHub stars](https://img.shields.io/github/stars/almende/vis.svg)](https://github.com/almende/vis/stargazers)

[![GitHub issues](https://img.shields.io/github/issues/almende/vis.svg)](https://github.com/almende/vis/issues)
[![Percentage of issues still open](http://isitmaintained.com/badge/open/almende/vis.svg)](http://isitmaintained.com/project/almende/vis "Percentage of issues still open")
[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/almende/vis.svg)](http://isitmaintained.com/project/almende/vis "Average time to resolve an issue")
[![Pending Pull-Requests](http://githubbadges.herokuapp.com/almende/vis/pulls.svg)](https://github.com/almende/vis/pulls)

[![Code Climate](https://codeclimate.com/github/almende/vis/badges/gpa.svg)](https://codeclimate.com/github/almende/vis) 

## 安装

通过 npm 安装：

    $ npm install vis

通过 bower安装：

    $ bower install vis

通过 cdnjs 链接： http://cdnjs.com

或者从这个GitHub项目中下载这个库：
[https://github.com/almende/vis.git](https://github.com/almende/vis.git).

## 加载

为了使用这个组件，在你的网页中应该包含vis库的JavaScript文件和CSS文件：

```html
<!DOCTYPE HTML>
<html>
<head>
  <script src="webroot/vis/dist/vis.js"></script>
  <link href="webroot/vis/dist/vis.css" rel="stylesheet" type="text/css" />
</head>
<body>
  <script type="text/javascript">
    // ... 加载一个可视化视图
  </script>
</body>
</html>
```

或者通过require.js来加载 vis.js。注意： vis.css 也必须被加载。

```js
require.config({
  paths: {
    vis: 'path/to/vis/dist',
  }
});
require(['vis'], function (math) {
  // ... 加载一个可视化视图
});
```


时间线可以实例化为：

```js
var timeline = new vis.Timeline(container, data, options);
```

这里的 `container` 是一个 HTML 元素，`data` 是一个数据或者DataSet数组，
`options` 是一个可选项，它是一个定义这个组件配置参数的一个object对象。

## 示例

加载时间线的基本示例如下所示。更多的示例请查看这个项目的
[示例库](https://github.com/almende/vis/tree/master/examples)。

```html
<!DOCTYPE HTML>
<html>
<head>
  <title>Timeline basic demo</title>
  <script src="vis/dist/vis.js"></script>
  <link href="vis/dist/vis.css" rel="stylesheet" type="text/css" />

  <style type="text/css">
    body, html {
      font-family: sans-serif;
    }
  </style>
</head>
<body>
<div id="visualization"></div>

<script type="text/javascript">
  var container = document.getElementById('visualization');
  var data = [
    {id: 1, content: 'item 1', start: '2013-04-20'},
    {id: 2, content: 'item 2', start: '2013-04-14'},
    {id: 3, content: 'item 3', start: '2013-04-18'},
    {id: 4, content: 'item 4', start: '2013-04-16', end: '2013-04-19'},
    {id: 5, content: 'item 5', start: '2013-04-25'},
    {id: 6, content: 'item 6', start: '2013-04-27'}
  ];
  var options = {};
  var timeline = new vis.Timeline(container, data, options);
</script>
</body>
</html>
```

## 搭建

从源码开始搭建这个库，先从GitHub上克隆这个项目

    $ git clone git://github.com/almende/vis.git

源码使用了node的模块模式（require 和 module.exports）来组织依赖关系。
为了安装所有的依赖库并搭建这个库，在项目的根目录处运行`npm install`指令。

    $ cd vis
    $ npm install

然后，项目可以建立运行：

    $ npm run build

要自动重建源文件中的更改，可以使用

    $ npm run watch

这样做可以在发生变化时构建和压缩这个库。压缩过程相对较慢，所以当只需要非压缩库时，可以运行`watch-dev` 脚本替换：

    $ npm run watch-dev

## 自定义搭建

`dist`文件夹包含`vis.js`的捆绑版本，以便在浏览器中直接使用。这些捆绑库包含所有可视化，并包含像`*hammer.js* `和 `*moment.js*`等外部依赖项。

`vis.js`的源代码由`commonjs`模块组成，这样做可以方便使用像[Browserify](http://browserify.org/) 或 [Webpack](http://webpack.github.io/)这样的工具自定义创建捆绑版本。这可以只捆绑一个像时间轴的可视化方法，或者将vis.js绑定为你自己的浏览器Web应用程序的一部分。

*注意，从v4开始，必须使用hammer.js 版本2。*

### 先决条件

在构建库之前你需要：

- 在你的操作系统中安装 *node.js* 和 *npm* ：https://nodejs.org/
- 使用npm安装以下模块： `browserify`、`babelify` 和 `uglify-js`:

  ```
  $ [sudo] npm install -g browserify babelify uglify-js
  ```

- 下载或者克隆 vis.js 项目：

  ```
  $ git clone https://github.com/almende/vis.git
  ```

- 通过在项目根目录运行`npm install`指令来安装vis.js的依赖库：

  ```
  $ cd vis
  $ npm install
  ```

### 自定义搭建的示例

#### 例1: 捆绑单一的可视化类型

举个例子，创建一个仅包含时间线和数据集的捆绑版本，在工程根目录处创建一个命名为**custom.js**的索引文件，包含：

```js
exports.DataSet = require('./lib/DataSet');
exports.Timeline = require('./lib/timeline/Timeline');
```

然后使用browserify创建一个自定义捆绑，像：

    $ browserify custom.js -t [ babelify --presets [es2015] ] -o dist/vis-custom.js -s vis
    
这样就会生成一个自定义捆绑版本 *vis-custom.js*，它会公开一个命名空间`vis`，这个命名空间只包含 `DataSet` 和 `Timeline`。 这个生成的捆绑版本可以使用uglifyjs来压缩：

    $ uglifyjs dist/vis-custom.js -o dist/vis-custom.min.js

这个自定义捆绑版本现在就可以像这样加载：

```html
<!DOCTYPE HTML>
<html>
<head>
  <script src="dist/vis-custom.min.js"></script>
  <link href="dist/vis.min.css" rel="stylesheet" type="text/css" />
</head>
<body>
  ...
</body>
</html>
```

#### 例2：排除外部库

The default bundle `vis.js` is standalone and includes external dependencies such as *hammer.js* and *moment.js*. When these libraries are already loaded by the application, vis.js does not need to include these dependencies itself too. To build a custom bundle of vis.js excluding *moment.js* and *hammer.js*, run browserify in the root of the project:

    $ browserify index.js -t [ babelify --presets [es2015] ] -o dist/vis-custom.js -s vis -x moment -x hammerjs

This will generate a custom bundle *vis-custom.js*, which exposes the namespace `vis`, and has *moment.js* and *hammer.js* excluded. The generated bundle can be minified with uglifyjs:

    $ uglifyjs dist/vis-custom.js -o dist/vis-custom.min.js

The custom bundle can now be loaded as:

```html
<!DOCTYPE HTML>
<html>
<head>
  <!-- load external dependencies -->
  <script src="http://cdnjs.cloudflare.com/ajax/libs/moment.js/2.17.1/moment.min.js"></script>
  <script src="http://cdnjs.cloudflare.com/ajax/libs/hammer.js/2.0.8/hammer.min.js"></script>

  <!-- load vis.js -->
  <script src="dist/vis-custom.min.js"></script>
  <link href="dist/vis.min.css" rel="stylesheet" type="text/css" />
</head>
<body>
  ...
</body>
</html>
```

#### 例3：捆绑 vis.js 作为你应用（commonjs）的一部分

When writing a web application with commonjs modules, vis.js can be packaged automatically into the application. Create a file **app.js** containing:

```js
var moment = require('moment');
var DataSet = require('vis/lib/DataSet');
var Timeline = require('vis/lib/timeline/Timeline');

var container = document.getElementById('visualization');
var data = new DataSet([
  {id: 1, content: 'item 1', start: moment('2013-04-20')},
  {id: 2, content: 'item 2', start: moment('2013-04-14')},
  {id: 3, content: 'item 3', start: moment('2013-04-18')},
  {id: 4, content: 'item 4', start: moment('2013-04-16'), end: moment('2013-04-19')},
  {id: 5, content: 'item 5', start: moment('2013-04-25')},
  {id: 6, content: 'item 6', start: moment('2013-04-27')}
]);
var options = {};
var timeline = new Timeline(container, data, options);
```

The application can be bundled and minified:

    $ browserify app.js -o dist/app-bundle.js -t babelify
    $ uglifyjs dist/app-bundle.js -o dist/app-bundle.min.js

And loaded into a webpage:

```html
<!DOCTYPE HTML>
<html>
<head>
  <link href="node_modules/vis/dist/vis.min.css" rel="stylesheet" type="text/css" />
</head>
<body>
  <div id="visualization"></div>
  <script src="dist/app-bundle.min.js"></script>
</body>
</html>
```

#### 例4：将vis.js组件直接集成到Webpack构建中

You can integrate e.g. the timeline component directly in you webpack build.
Therefor you just import the component-files from root direcory (starting with "index-").

```js
var visTimeline = require('vis/index-timeline-graph2d');

var container = document.getElementById('visualization');
var data = new DataSet();
var timeline = new Timeline(container, data, {});
```

To get this to work you'll need to add the some babel-loader-setting:

```js
module: {
	loaders: [{
		test: /node_modules[\\\/]vis[\\\/].*\.js$/,
		loader: 'babel',
		query: {
			cacheDirectory: true,
			presets: ["es2015"],
			plugins: [
				"transform-es3-property-literals",
				"transform-es3-member-expression-literals",
				"transform-runtime"
			]
		}
	}]
}
```

## 测试

要测试库，首先安装项目依赖关系：

    $ npm install

然后运行测试：

    $ npm run test

## 许可

Copyright (C) 2010-2017 Almende B.V. and Contributors

Vis.js 是双重授权，包括

  * The Apache 2.0 License
    http://www.apache.org/licenses/LICENSE-2.0

和

  * The MIT License
    http://opensource.org/licenses/MIT

Vis.js可以按照许可证分发。
