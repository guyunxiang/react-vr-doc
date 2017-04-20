# 起步

在开始第一个 React VR 应用前，你需要安装一些软件用来构建和管理 React VR 应用：**Node.js** 和 **React VR CLI 工具。**

#### 安装 Node.js

如果你已经安装了 Node.js，请确保你的 Node.js 版本是4.0以上。

* Mac：在 Mac 上，我们建议使用 [Homebrew](http://brew.sh/) 安装 Node.js。

* Windows：从 Node.js [官网下载](https://nodejs.org/en/download/) 安装 Node.js。

* Linux：去 nodejs.org 包管理页面找到你 Linux 系统分布的具体指示。

#### 创建第一个项目

我们使用 React VR 命令行工具创建一个项目叫：“WelcomeToVR”。这个命令行工具会新建一个文件夹，包含 React VR的项目骨架，并且按照所必要的依赖包。

  1. 如果你的终端仍然在运行 npm，请按 `CTRL+C` 终止掉。

  2. 进入到你将要新建项目的目录下

  3. 全局安装 React VR CLI 工具，输入：

```bash
npm install -g react-vr-cli
```

  4. 使用 React VR CLI 工具创建一个 `WelcomeToVR` 项目文件夹，并且安装必须的依赖包，输入：

```bash
react-vr init WelcomeToVR
```

  5. 进入新创建的 `WelcomeToVR` 项目目录。

```bash
cd WelcomeToVR
```

  6. 使用 start 命令来初始化本地服务，输入：

```bash
npm start
```

  7. 浏览器输入：[http://localhost:8081/vr/index.html](http://localhost:8081/vr/index.html) 你就可以看到如下的场景：

![](https://facebook.github.io/react-vr/img/hellovr.jpg)

哈喽！

在浏览器上点击和拖动或者在移动设备上可以看到更多。

如果你使用的浏览器支持 webVR，例如 [Carmel Developer Preview browser from Oculus](https://www.oculus.com/experiences/gear-vr/1290985657630933/)，你可以戴上VR头盔，探索完整的 VR 世界。关于浏览器 VR 能力的更多信息，请参见 VR 浏览器主题。

我们开始探索下一个主题，探索如何展现这一幕的代码实现。

