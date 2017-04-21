# 你好世界

按照我们一直以来的传统，我们第一个 React VR 应用不做其他功能，仅在全景中展示一个"hello"，你可以项目文件夹中查看源码文件 `index.vr.js` 。这个文件是你的 React VR 项目的入口文件。

```javascript
'use strict';
import React from 'react';
import { AppRegistry, asset, Pano, Text, View } from 'react-vr';

class WelcomeToVR extends React.Component {
  render() {
    // Displays "hello" text on top of a loaded 360 panorama image.
    // Text is 0.8 meters in size and is centered three meters in front of you.
    return (
      <View>
        <Pano source={asset('chess-world.jpg')}/>
        <Text
          style={{
            backgroundColor: '#777879',
            fontSize: 0.8,
            layoutOrigin: [0.5, 0.5],
            paddingLeft: 0.2,
            paddingRight: 0.2,
            textAlign: 'center',
            textAlignVertical: 'center',
            transform: [{translate: [0, 0, -3]}],
          }}>
          hello
        </Text>
      </View>
    );
  }
};

AppRegistry.registerComponent('WelcomeToVR', () => WelcomeToVR);
```

React 应用会分离成多个组件的形式，结构元素定义了你的应用如何渲染各个部分以及如何响应用户输入来更新组件自身。这段代码声明了你的顶级组件WelcomeToVR以及确定了如何呈现它。

我们的代码一开始是导入依赖，然后声明 WelcomeToVR 组件，包含如何渲染它。代码的结尾，使用 `AppRegistry` 注册我们声明的组件。最后一部分代码只要顶级组件在你的程序中即可，你可以放心的忽略它。

你可能注意到了，代码的内容中，`return` 的内容并不是真正的 JavaScript。类似于`<View>`，`<Pano>`，`<Text>`的声明是使用 JSX实现的，可以在 JavaScript 中插入类似 XML 语法的结构，JSX 允许你清晰的描述你的 UI，下面我们将详细的讨论它们。

让我们来检查一下我们组件的结构，我们返回了一个 `View` 组件，它有两个子组件：`Pano` 和 `Text` ：

* `Pano` 在你的VR世界里创建了一个盒子，盒子内部 360 度渲染图片。这个组件渲染了你在示例中所能看到四周的环境

* `Text` 在 3D 空间中渲染了一串字符，这个特定的 `Text` 标签将渲染一个大大的文字出现在 VR 世界的中间

* `View` 组件通常作为一个容器，它包含着其他组件，可以用于提供间距或者 UI 设计的需求，我们示例中的组件创建了一个`View` 包裹着 `Pano` 和 `Text` 标签

每一个 React 组件都必须只返回一个元素，所以我们示例中的组件在两个子组件的外面需要包裹一个 `View`

想要更好的理解代码到底做了什么，你可以尝试修改部分代码。在 起步 中，我们创建了一个项目叫 WelcomeToVR，那么我们来把'' hello"的提示语改为"welcome"，在 `Text` 标签闭合内部的文本字符串，把它改成"welcome"，如果你的 npm 正在运行中，那么你刷新页面就可以查看更改后的效果了。

# JSX 和 ES6 - 发生了什么？

现在的 web 应用开发很大程度上依赖各种工具，例如各种解析，JavaScript 预处理等。这么做的原因有很多，例如：打包多个 JavaScript 代码文件，或者实现新的语言特性，这也正是 React 命令行所做的。转换这些代码来实现 JSX 和 ES6：

* **JSX** 通过类似 XML 的标签语法扩展了JavaScript，允许你像 HTML 那样嵌套你的组件。JSX 使得你的 React 代码更容易编写。你可以在 [React 官网](https://facebook.github.io/react/docs/jsx-in-depth.html)了解更多内容。如果你坚持一定要在你的项目中仅仅使用 JavaScript，你也可以[不使用 JSX 在你的 React 项目中](https://facebook.github.io/react/docs/react-without-jsx.html)。

* **ES6**，又称之为 ES2015，代表了 ECMA Script 6代语法，它对现有的 JavaScript 进行了改进。如今已经是官方的唯一标准，但是还没有被所有的浏览器所支持，所以进行 ES6代码的转换是有必要的。React Native 附带了对 ES2015 的支持，所以你可以放心的使用它而不用担心兼容性。`import`，`from`，`class`，`extends` 以及 `() =>` 这些语法示例都是 ES2015 的新特性。[点击这里](https://babeljs.io/docs/learn-es2015/) 查看关于 ES2015 新特性更好的介绍。

类似这样的语法 `<Text style={{ fontSize: 0.8, ... }}>hello</Text>` 就是使用了 JSX， 它最终会被转化成 JavaScript。有关更多信息，请参见 [React VR 概述](https://facebook.github.io/react-vr/docs/react-vroverview.html)。

# AppRegistry

我们 Hello World 示例中定义了一个新的组件 `WelcomeToVR`，同时它通过 `AppRegistry` 进行了注册。`AppRegistry` 告诉了 React VR 哪一个组件才是整个应用的根组件。你不需要了解 AppRegistry 太多，在一个项目中应该只会有一次`AppRegistry.registerComponent`。包含上面的那段代码，你可以整个的粘贴到你的 `index.vr.js` 文件中并且运行起来。

当你正在开发一个 React VR 应用时，你可能会开发很多新的组件出来，任何可以在屏幕上看到的都是组件。一个组件可以很简单，它唯一的要求就是必须要有一个 Render 函数来返回一些 JSX的语法标签。

