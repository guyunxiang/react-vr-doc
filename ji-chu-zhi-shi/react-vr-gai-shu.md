# React VR 概述

React 是 Facebook 的一个开源 JavaScript 项目，可以用来方便的创建交互式的用户界面。React VR 让 React 更进了一步，可以用来创建用户界面和 3D 虚拟现实场景。

在本节中，我们将强调 React VR 的核心优势及概念。

#### JSX 和 声明式的用户界面

React 吸引人的一个特点就是它结合了声明式的 UI 元素代码，以更为优雅的方式来操纵代码。UI 元素以组件标签的形式声明，看起来就像 HTML 一样。举个例子：这个标签 `<Greeting name='Joe'/>` 可以用来描述一个问候的 UI 组件，同时需要一个 name 作为参数。因为 JSX 的帮助，像这样的标签就可以直接的插入 JavaScript 中。

[JSX](https://facebook.github.io/react/docs/introducing-jsx.html) 是一种 JavaScript 的语法扩展；它会被 React Native 包预处理为 JavaScript 代码。JSX 能够比直接写 JavaScript 代码更为优雅的声明用户界面。

```javascript
<MyButton color="blue" shadowSize={2}>
  Click Me
</MyButton>
```

编译为：

```javascript
React.createElement(
  MyButton,
  {color: 'blue', shadowSize: 2},
  'Click Me'
)
```

并不是强制使用 JSX，它更加利于代码的可读性。关于[ JSX 的更多细节](https://facebook.github.io/react/docs/jsx-in-depth.html)见 React 网站。

#### React 核心概念

使用 React 必需要了解一些术语和核心概念。这里快速列举了最为重要的概念以及他们之间是如何相互影响的。

* **Components** - 组件是可复用的 UI 元素，它可以以标签的形式使用，例如 `<Greeting />` 。React Native 提供了一些内置的组件例如：`Text` 和 `Image`。自定义的组件可以通过 `React.Component` 来声明。每一个自定义的组件都包含一个 `render()` 函数，它只返回一个孩子元素，用以完整的描述组件的内容。

* **Props** - 组件可以接受一些参数，例如 `<Greeting name='Rexxar' />` 中的 `name` 。类似的这种参数被称之为属性或者 props，可以通过 `this.props` 来访问它们。上文中的例子，name ，可以用 `{this.props.name}` 访问。你可以了解更多关于这种交互式组件 props 和 State 的[详细文档](https://facebook.github.io/react-vr/docs/components-props-and-state.html)。

* **State** -组件可以通过维护内部的状态来影响组件的显示。当 state 的数据发生变化，组件会重新刷新自己。根据 React 的约定，所有可以修改的 state 都在 `this.state` 对象上。组件只能够通过专有的 `setState` 方法来修改 state，例如：

```javascript
this.setState({myStateVariableCounter: 10})
```

* **Events** - 组件可以发生事件，当它触发时可以提供特定的 UI 动作。例如：`View` 组件在光标进入或者离开这块区域时会分别触发 `onEnter` 和 `onExit` 事件，可以在组件声明式适当添加一些交互当这些事件触发时。举个例子：

```javascript
<View onEnter={() => this.setState({hasFocus: true})}>
```

* **Layout** - React 使用 flexbox 算法和布局规则将组件放置在一个二维平面上。这总布局考虑组件的尺寸，要么计算、要么指定组件的宽度和高度，以及控制组件的样式及属性，例如 `alignItems` 。更多描述见 [Layout 和 Style](https://facebook.github.io/react-vr/docs/layout-and-style.html)。

* **Style** - 样式对象控制了组件的显示和布局。它们通常通过指定一个样式对象，例如：

```javascript
<View style={{width: 100, height: 100, backgroundColor: 'skyblue'}}/>
```

通过这种方式而不是指定所有组件的行内属性。style 对象可以提取出来，通过 `StyleSheet.create` 来声明。这种提取出来的样式表可以被组件重复使用。虽然 React StyleSheet 和 CSS 共享一些属性名，但实际上它们并不直接相关。

下面来更详细的描述这些项目。

#### React 生态系统

虽然最初的 web 开发是非常简化的，现在的 React 生态圈已经发展到包含以下几个产品：

* React - 最初的库，它的目标是用来在 web 浏览器中创建 DOM。

* React Native - 目标是通过原生的组件可以开发 IOS 和 Android 的APP应用。React Native 的构建是在 React 的核心基础之上。

* React VR - 一个我们正在学习的新库，这个可以用来开发 VR 的界面。React VR 的构建是在 React Native 框架基础之上。

当它在浏览器中运行时，React VR 在结构上较 React 而言，与 React Native 有更多相同点。它支持需要相同的标签例如 `<View>` 和 `<Text>` 。除了 2D 布局，它还包含了 3D 场景、转换和全景的概念，允许对象被放置在 3D 空间来呈现虚拟现实场景。

好的技术实现，React VR 使用了一个简单的 OVRUI 库，它使用了当前流行的 three.js JavaScript 3D 引擎。Three.js 在浏览器中运行，并通过 WebGL 呈现场景。通过 VR 头盔可以访问所有 Web VR 的接口，它可以在 Riff、GearVR 或者其他设备中显示。React VR 则不然，它不是必须要 VR 头盔才能运行，它也可以在浏览器或者移动手机上创建交互式的360度全景体验。

React Native 的核心概念也同样适用于 React VR。这里列举了一些核心概念，详情链接以及更多信息的介绍。

#### React Native Packager

React 的 JavaScript 代码会在浏览器中运行前进行预编译处理。这预处理就是通过 React Native Packager 执行的。这个工程类似 Browserify 和 Webpack，同时提供了类似 CommonJs 的模块系统，JavaScript 编译（ES6，Flow，JSX），构建和静态资源加载。

