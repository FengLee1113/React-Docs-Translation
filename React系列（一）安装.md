# React系列（一）安装
原文地址：[原文][]

本系列是针对[React][]文档进行的翻译，因为自己在学习react的时候，最开始通过看博客或者论坛等中文资料，有些内容是零零散散的接收，并没有给自己带来很好的效果，所以后来决定把文档的原文从头到尾看一遍。目前为止原文文档也看的差不多了，自己的英文水平也有限，看的也是似懂非懂，但是却比在博客或者其他途径得来的零散的效果要好一些，而且原文文档是最新的，而找到的中文资料都是其他人之前翻译或者针对之前的文档写出来的一些解决方案，对更新后的内容并没有进行更新，基于这样的想法，自己也本着能够更加深入的学习，所以决定对文档进行一个大概的翻译，第一次做这些事情，不知道自己能坚持多久，也不知道自己能翻译到什么程度，错误之处还望多多指正，希望能够坚持下去。废话不多说，进入正题。

## **安装**
React是灵活的，并且可以应用到各种各样的项目中。你可以使用它创建一个新的项目，但是，你也可以在不用重新编写的前提下，逐步的将它引入到现有的代码库中。
#**初尝React**
如果你只是对React感兴趣，你完全可以使用CodePen。尝试这从这个[Hello World示例][]开始吧。你不用安装任何东西，只需要对代码进行修改，然后看看它是否会起作用。

如果你更喜欢使用自己的文本编辑器，可以下载[这个HTML文件][]，编辑它，然后在本地通过浏览器打开。它会执行一个缓慢的运行时代码转换，所以不要在生产环境使用它。
## **创建一个单页面应用**
[Create React App][]（译者注：facebook提供的一个工具集）是开始创建React单页应用最好的一种方式。它已经为你设置好了开发环境，这样你就可以使用到最新的Javascript特性，提供一个良好的开发体验，并且可以优化你的生产环境应用。
>npm install -g create-react-app
create-react-app hello-world
cd hello-world
npm start

Create React App 不会处理后端逻辑或者是数据库；它只是创建了一个前端构建管道，所以你可以使用它配合任何你想使用的后端。它的底层是使用[Webpack][]，[Babel][]and [ESLint][]，但是已经为你配置好了。
## **在已有应用中加入React**
你不必为了开始使用React而重写原来的应用。

我们推荐你将React添加到你应用的一小部分中，比如一个个人小部件，这样你可以观察一下是否它能在你的应用场景下良好的运行。

尽管React可以在[没有构建管道][]（build pipeline）的情况下使用，然而我们还是推荐将构建管道配置起来以便提高生产力。一个典型的现代构造管道包括下面几部分：

 - 一个包管理器，比如[Yarn][]或者[npm][]。它可以让您利用庞大的第三方软件包生态系统，轻松安装或更新它们。

 - 一个构建工具，比如[Webpack][]或者[Browserify][]。它允许您编写模块化代码并将其捆绑在一起成为小包以优化加载时间。

 - 一个编译器，比如[Babel][]，它可以让您编写仍旧适用于旧版浏览器的现代JavaScript代码。

### **安装React**
我们推荐使用[Yarn][]或者[npm][]来管理前端依赖。如果你是包管理工具的新手，[Yarn文档][]是一个好的开始的地方。

使用Yarn安装React，运行下面的命令：
>yarn init
yarn add react react-dom

使用npm安装React，运行下面的命令:
>npm init
npm install --save react react-dom

Yarn和npm都是从[npm registry][]下载所需要的包。
### **启用ES6和JSX**
为了在你的Javascript代码中使用ES6和JSX，我们推荐配合Babel使用React。ES6是一组可以使开发变得更简单的现代化的JavaScript特性，JSX是对React的很好的JavaScript语言的扩展。

Babel[设置说明][]解释了如何在许多不同的构建环境中配置Babel。确保你已经安装了[babel-preset-react][]和[babel-preset-es2015][] 并且已经在你的[.babelrc 配置][]中启用了他们，这样就准备就绪了。
### **使用ES6和JSX的Hello World**
我们建议使用像webpack或Browserify这样的构建器，以便您可以编写模块化代码，并将其打包在一起成为小包，以优化加载时间。

最小的React例子是像下面这样：
``` javascript
import React from 'react';
import ReactDOM from 'react-dom';
ReactDOM.render(
	<h1>Hello, world!</h1>,
	document.getElementById('root')
);
```
这段代码会渲染到id为root的DOM元素中，所以在你的HTML文件中的某处需要```<div id="root"></div>```。

类似的，你也可以在使用其他Javascript UI库所写的现有应用中的某处，将一个React组件渲染到一个DOM元素上。

### **开发环境版和生产环境版**
默认的，React包括了许多有用的警告。这些警告在开发环境中是非常有用的。然而，他们会让React变得很大并且很慢，所以要确保在部署应用的时候要使用生产环境版。

**Brunch**

想要使用Brunch创建一个优化的生产构建，只需要在构建命令中添加```-p ```标识。更多细节参看[Brunch docs][]。

**Browserify**

运行Browserify，将``` NODE_ENV ```环境变量设置成``` production```，使用[UglifyJS][]作为构建的最后一步，这样只在开发环境生效的代码就会被剥离出来。

**Create React App**

如果使用[Create React App][]，```npm run build ```会在应用的``` build```文件夹下面生成一份优化后的代码。

**Rollup**

使用[rollup-plugin-replace][]和[rollup-plugin-commonjs][]一起（按照顺序）移除开发专用的代码。[这里][]有完整的设置案例。

**Webpack**

像这个[指南][]描述的这样将```DefinePlugin```和```UglifyJsPlugin```包含到生产环境的Webpack配置中。


### **使用CDN**
如果不想使用npm管理客户端包，``` react```和``` react-dom```的npm包在```dist```文件夹下面也提供了单个文件的分发，他们托管在CDN上：
``` 
<script src="https://unpkg.com/react@15/dist/react.js"></script>
<script src="https://unpkg.com/react-dom@15/dist/react-dom.js"></script>
``` 
上面的版本只适合开发环境，不适合生产环境。压缩并优化后的React可用生产版本在：
```
<script src="https://unpkg.com/react@15/dist/react.min.js"></script>
<script src="https://unpkg.com/react-dom@15/dist/react-dom.min.js"></script>
```
如果想加载特定版本的```react ```和 ```react-dom```，可以将15替换为想加载版本的版本号。
如果使用Bower，React可以通过```react```包获取到。


--------
[React]:https://facebook.github.io/react
[原文]:https://facebook.github.io/react/docs/installation.html
[Hello World示例]:http://codepen.io/gaearon/pen/rrpgNB?editors=0010&_blank
[这个HTML文件]:https://facebook.github.io/react/downloads/single-file-example.html
[Create React App]:http://github.com/facebookincubator/create-react-app
[Webpack]:https://webpack.js.org
[Babel]:http://babeljs.io
[ESLint]:http://eslint.org
[没有构建管道]:https://facebook.github.io/react/docs/react-without-es6.html
[Yarn]:https://yarnpkg.com
[npm]:https://www.npmjs.com
[Browserify]:http://browserify.org/
[Yarn文档]:https://yarnpkg.com/en/docs/getting-started
[npm registry]:http://npmjs.com/
[设置说明]:https://babeljs.io/docs/setup/
[babel-preset-react]:http://babeljs.io/docs/plugins/preset-react/#basic-setup-with-the-cli-
[babel-preset-es2015]:http://babeljs.io/docs/plugins/preset-es2015/#basic-setup-with-the-cli-
[.babelrc 配置]:http://babeljs.io/docs/usage/babelrc/
[Brunch docs]:http://brunch.io/docs/commands
[UglifyJS]:https://github.com/mishoo/UglifyJS
[rollup-plugin-replace]:https://github.com/rollup/rollup-plugin-replace
[rollup-plugin-commonjs]:https://github.com/rollup/rollup-plugin-commonjs
[这里]:https://gist.github.com/Rich-Harris/cb14f4bc0670c47d00d191565be36bf0
[指南]:https://webpack.js.org/guides/production-build/