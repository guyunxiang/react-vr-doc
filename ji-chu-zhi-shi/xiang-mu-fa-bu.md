# 项目发布

#### 创建发布资源

一旦你创建了一个引人关注的 VR 体验，也许你会想要把它分享到网络上。React VR 自带了一个脚本，可以把所以代码打包成几个文件，你可以把打包后的文件放在你的 web 服务器上。在你的项目根目录下运行：

```bash
npm run bundle
```

这回创建一个新的文件夹叫 `build`，里面是你应用编译版本的文件。这些文件可以放在 web 服务器上就可以工作，不会有任何改变，只要它们被放置在相同的目录中。

如果你引用了其他外部资源 asset\(\)，你也需要复制这些文件到你的 static\_assets 目录和文件，这样的应用就可以引用到这些资源。关于这点，你的目录结构应该类似于这样：

```bash
Web Server
├─ static_assets/
│
├─ index.html
├─ index.bundle.js
└─ client.bundle.js
```

如果你想要单独指定 JavaScript 文件的位置，你可以通过修改 `index.html` 来实现。请确保你的 `script` 标签位置在你的 client.bundle.js 上面，同时在 `index.bundle.js` 中的 `ReactVR.init()` 包含了正确的路径。

如果你想要单独指定你的外部资源文件位置，例如 CDN 资源，你可以在 `ReactVR.init()` 中指定根目录的 `assetRoot` 配置。例如：你的外部资源引用 `http://cdn.example.com/vr_assets/`，你可以给这个方法调用第三个参数：

```javascript
ReactVR.init(
  'path/to/index.bundle.js',
  document.body,
  { assetRoot: 'https://cdn.example.com/vr_assets/' }
);
```

#### 集成现有的网页

如果你想在一个现有的网站中嵌入 VR 体验，较为推荐的方式是使用 iframe 标签。设置 src 属性到你的 VR 项目的 inde.html 文件，同时为 iframe 设置一个合适的大小。

