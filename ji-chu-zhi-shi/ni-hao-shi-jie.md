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

