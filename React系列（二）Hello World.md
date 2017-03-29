#Hello World
#表头
开始React最简单的方式就是在CodePen上使用[Hello World示例][1]。无需安装任何环境，只需要在其他标签页打开它然后跟着我们的例子去做。如果更喜欢使用本地开发环境，可以访问[安装][2]页面。

最小的React例子如下：
	`ReactDOM.render(
		<h1>Hello, world!</h1>,
		document.getElementById('root')
	);`

它会在页面上渲染一个标题'Hello World'。

接下来的几部分会逐步的介绍如何使用React。我们会查验React应用的构建块：元素和组件。一旦掌握了他们，就可以使用小的可复用片段创建复杂的应用。

#关于Javascript的说明
React是一个Javascript库，所以它需要你对Javascript开发语言有一个基本的了解。如果觉得不自信，我们推荐先掌握[Javascript的知识][3]，这样才能更容易的跟上脚步。

在例子中也使用了一些ES6的语法。我们尽量谨慎的去使用ES6，因为它相对来说还是比较新的，但是还是鼓励先去熟悉一下[箭头函数][4]、[类][5]、[模板字符串][6]、[let][7]和[const][8]声明。可以使用在线[Babel转换器][9](Babel REPL)查看ES6的代码编译。

[1]:http://codepen.io/gaearon/pen/ZpvBNJ?editors=0010 "example"
[2]:http://blog.csdn.net/feng1327/article/details/67676296
[3]:https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript "Javascript API"
[4]:https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions "arrow function"
[5]:https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes "es6 classes"
[6]:https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Template_literals "Template_literals"
[7]:https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let "let"
[8]:https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const "const"
[9]:http://babeljs.io/repl/#?babili=false&evaluate=true&lineWrap=false&presets=es2015%2Creact&experimental=false&loose=false&spec=false&code=const%20element%20%3D%20%3Ch1%3EHello%2C%20world!%3C%2Fh1%3E%3B%0Aconst%20container%20%3D%20document.getElementById('root')%3B%0AReactDOM.render(element%2C%20container)%3B%0A "Babel REPL"
