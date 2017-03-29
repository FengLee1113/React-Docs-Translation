# React文档翻译系列（三）JSX简介

先来看一下下面的变量声明：
```
const element = <h1>Hello world!</h1>
```
这种有趣的标签语法既不是字符串也不是HTML。

这种形式被称作JSX，他是Javascript的一种扩展语法。我们推荐在React中使用这种形式来描述UI该是什么样子的。JSX可能会让你想起某种模板语言，但是它具有Javascript的全部功能。

JSX会生产出React“元素”。我们将在[下一部分](https://facebook.github.io/react/docs/rendering-elements.html)来探索如何将它渲染到DOM上。接下来，您可以找到JSX的基础知识，以帮助您开始使用。

## **JSX中嵌入表达式**

您可以在JSX中，通过一对大括号嵌入任何的[Javascript表达式](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Expressions)。

比如`2+2`,`user.firstName`,和`formatName(user)`，这些都是可用的表达式。
```
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);

ReactDOM.render(
  element,
  document.getElementById('root')
);
```
[在CodePen中尝试。](http://codepen.io/gaearon/pen/PGEjdG?editors=0010)

为便于阅读，我们将JSX分隔成多行。我们推荐使用括号将JSX包裹起来，尽管这不是必须的，因为这样可以避免[分号自动插入](http://stackoverflow.com/q/2846283)的陷阱。

## **JSX也是一种表达式**

编译之后，JSX表达式就变成了常规的Javascript对象。

这意味着你可以在`if`语句或者是`for`循环中使用JSX，用它给变量赋值，当做参数接收它，或者作为函数的返回值。
```
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```
## **用JSX指定属性**

您可以使用引号来指定字符串作为属性：
```
const element = <div tabIndex="0"></div>;
```
您也可以在一个属性中通过花括号嵌入一个Javascript表达式：
```
const element = <img src={user.avatarUrl}></img>;
```
在属性中嵌入Javascript表达式的时候不要使用引号来包裹花括号。否则JSX会将属性当做一个字符串而不是表达式。在同一个属性中，您可以选择使用引号（字符串的值）或者是花括号（表达式），但是不能同时使用。

## **使用JSX指定子元素**

如果标签是空的，您应该像XML一样立即使用`/>`关闭它：
```
const element = <img src={user.avatarUrl} />;
```
JSX标签可能包含子元素：
```
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```
> **警告**
 由于JSX相对HTML来说更接近于Javascript，所以React DOM使用驼峰方式为属性命名来取代HTML的属性名。
 例如，在JSX中，`class`变成了[`className`](https://developer.mozilla.org/en-US/docs/Web/API/Element/className)，`tabindex`变成了[`tabIndex`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/tabIndex)。

## JSX防止了注入式攻击

在JSX中，嵌入用户输入是安全的：
```
const title = response.potentiallyMaliciousInput;
// This is safe:
const element = <h1>{title}</h1>;
```
默认的，React DOM在渲染通过JSX嵌入的任何内容之前，都会将他们的值进行转义。这样就确保了除非在你的应用中明确的写出来的内容，绝对不会注入其他任何内容。
在被渲染之前，所有的东西都被转义成为了字符串，这样就能帮助您防止[XSS（cross-site-scripting）](https://en.wikipedia.org/wiki/Cross-site_scripting)攻击。

## JSX表示对象

Babel将JSX编译成`React.createElement()`调用。

下面的两个例子是相同的：
```
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```
```
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```
`React.createElement()`会执行一些检查来帮助你写出没有bug的代码，但是它创建对象的原理是像下面这样：
```
// Note: 这是简化的结构
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world'
  }
};
```
这些对象被称作“React元素”。你可以把他们想象成为你想在屏幕上看到的东西的一种描述。React会读取这些对象，用他们来构建DOM，并且保持它们的不断更新。

我们将在下一部分来探索如何将React元素渲染到DOM上。

> **Tips**
我们建议您为选择的编辑器搜索“Babel”语法方案，以便ES6和JSX代码都能够被正确高亮的显示。