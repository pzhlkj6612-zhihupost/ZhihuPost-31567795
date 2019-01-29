![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-b77e62f2328e988eb1606cabad155977.jpg)

禁止转载。

禁止转载是指“禁止转载本文内容”，可以通过超链接的方式分享本文。

<br/>

本文章内容由我的这个回答处理而来：

[https://www.zhihu.com/question/58159898/answer/167682476](https://www.zhihu.com/question/58159898/answer/167682476)

本文章也存在于 GitHub 仓库：

[https://github.com/pzhlkj6612/ZhihuPost-31567795](https://github.com/pzhlkj6612/ZhihuPost-31567795)

<br/>

注意：

* 本文的内容是过时的；
* 我仅在 Windows 7/8.1/10 下的 Adobe CS4/CC 2017/CC 2018 对本文内容做了简要测试；
* 所有方法均由我从各个地方习得并测试，仅供参考，并不一定是最佳选择；
* 本文并不适合在小屏幕终端上阅读；
* 以下内容有难度，请你务必耐心；
* 有问题请及时指出。

----

# 目录

- [目录](#%E7%9B%AE%E5%BD%95)
- [概述](#%E6%A6%82%E8%BF%B0)
- [直接导出 GIF（仅介绍）](#%E7%9B%B4%E6%8E%A5%E5%AF%BC%E5%87%BA-gif%E4%BB%85%E4%BB%8B%E7%BB%8D)
- [用 Ps 配合 Ae 导出 GIF](#%E7%94%A8-ps-%E9%85%8D%E5%90%88-ae-%E5%AF%BC%E5%87%BA-gif)
- [用 AME 或 Pr 配合 Ae 导出 GIF](#%E7%94%A8-ame-%E6%88%96-pr-%E9%85%8D%E5%90%88-ae-%E5%AF%BC%E5%87%BA-gif)
- [Ps 与 AME 或 Pr 导出文件的效果对比](#ps-%E4%B8%8E-ame-%E6%88%96-pr-%E5%AF%BC%E5%87%BA%E6%96%87%E4%BB%B6%E7%9A%84%E6%95%88%E6%9E%9C%E5%AF%B9%E6%AF%94)
- [用 Ae 脚本导出 GIF（仅介绍）](#%E7%94%A8-ae-%E8%84%9A%E6%9C%AC%E5%AF%BC%E5%87%BA-gif%E4%BB%85%E4%BB%8B%E7%BB%8D)
- [异常处理](#%E5%BC%82%E5%B8%B8%E5%A4%84%E7%90%86)
- [注意事项](#%E6%B3%A8%E6%84%8F%E4%BA%8B%E9%A1%B9)
- [未解决的问题](#%E6%9C%AA%E8%A7%A3%E5%86%B3%E7%9A%84%E9%97%AE%E9%A2%98)
- [推荐](#%E6%8E%A8%E8%8D%90)
- [结尾](#%E7%BB%93%E5%B0%BE)

----

# 概述

制作 GIF 动画的方法很多，本文只讨论从 Ae 开始，如何实现 GIF 动画的导出。

在当前最新版本软件中，从最终结果来看，以下路径是质量较高且过程简易的：

```
Ae合成
  |
  < QuickTime 格式(GoPro CineForm 编码 质量 4) | 较低帧率 | 较低分辨率 >
  |
.mov 视频文件
  |
  < 导入 >
  |
Adobe Media Encoder
  |
  < “动画 GIF”格式 | 质量 100 >
  |
.gif 动画文件                     _______________________
  |
  < http://gifcompressor.com/ > ←对于机密文件，不要这样做
  |
更小的 .gif 动画文件               _______________________
```

<br/>

文中用到的视频素材来自：《[【大花豹】极乐净土](https://www.bilibili.com/video/av10397269/)》《[50帧又何妨（25FPS已重传）\(2\)](https://www.bilibili.com/video/av9198307/#page=2)》

----

# 直接导出 GIF（仅介绍）

早于 Creative Suite 5([CS5(10.0)](https://en.wikipedia.org/wiki/Adobe_After_Effects#History)) 版本的 Ae 支持导出 GIF 动画（[官方文档](https://helpx.adobe.com/cn/after-effects/kb/supported-file-formats-effects-cs4.html#main__Supported_video_and_animation_file_formats_)），但是你不应该继续使用旧版本 Ae，所以这一部分仅给出要点。我使用的是 Ae CS4(9.0.1)：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-b5c371feee1601b1a473f88e442fb7fd.jpg)

<br/>

自 CS5 版本开始，Ae 不再支持导出 GIF 动画了，现在`渲染队列`-`输出模块`打开`输出组件设置`，在`主要选项`-`格式`中找不到`动画 GIF`：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-6da37738cd74d11773d91f70734d991c.jpg)

[Adobe 官方的用户指南](https://helpx.adobe.com/cn/after-effects/user-guide.html) > [渲染和导出](https://helpx.adobe.com/cn/after-effects/user-guide.html?topic=/cn/zh-Hans/after-effects/morehelp/exporting_publishing_rendering.ug.js) > [渲染和导出基础知识](https://helpx.adobe.com/cn/after-effects/using/basics-rendering-exporting.html) > [支持的输出格式](https://helpx.adobe.com/cn/after-effects/using/basics-rendering-exporting.html#supported_output_formats) 中提到：

> 要创建动画 GIF 格式的影片，请首先从 After Effects 渲染和导出 QuickTime 影片。然后，将 QuickTime 影片导入 Photoshop，并且将影片导出为动画 GIF。

这表示，我们需要其它软件（例如 Ps）的帮助才能获得 GIF。其实不光是“QuickTime 影片”，通过其它的媒介（例如序列帧）最终也能得到 GIF，但为了避免内容变得杂乱，我有意去掉了“序列帧”相关的内容，感兴趣的朋友可以自己做尝试。

以下是 Ps、AME、Pr 三款软件配合 Ae 导出 GIF 动画文件的方法。要注意，这些方法不仅能用于处理 Ae 中的媒体，还能直接处理一般的视频文件；

----

# 用 Ps 配合 Ae 导出 GIF

**█ 特征**

操作较复杂，软件处理缓慢，操作耗时较长；

参数繁多，可设定 GIF 循环次数，可保留 Alpha 通道（透明度信息），以`视频帧`方式导入的素材会有长度限制。

（Photoshop 的内容我还没有完全弄明白，但目前已写出的内容是没有问题、经得起验证的）

<br/>

**█ 首先**

保存你的 Ae 项目文件，并将你的合成导出为 QuickTime 格式的视频（建议使用 GoPro CineForm 编码）：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-49bf6c1d1fab4c37f0acf938389d7f60.jpg)

如果你需要制作带 Alpha 通道的 GIF，要在事先做处理。导出 Ae 合成之前，单击`输出组件`后的链接，打开`输出组件设置`窗口。`主要选项`中，`格式`选择`QuickTime`，`视频输出`区域-`通道`选择`RGB+Alpha`（如果`RGB+Alpha`不可选，就需要切换到正确的编解码器，参考文末“[注意事项](#%E6%B3%A8%E6%84%8F%E4%BA%8B%E9%A1%B9)”）：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-323514efb5034765077ebccbc448b4c7.jpg)

通常，GIF 并不需要太高的分辨率和帧率，你可以在导出前进行额外的设置（这不影响原合成）。找到`渲染队列`面板中的合成，单击`渲染设置`后的链接，打开`渲染设置`窗口。将`合成“xxx”`区域中的`分辨率`改为 1/3、1/4 等；再将`帧速率`区域中的`使用此帧速率`选中，并为其指定一个更低的值（10 ~ 25）：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-1bc651dd01ddf76aa7070a52e0352506.jpg)

打开 Ps，先找到菜单栏 -`窗口`-`时间轴`以打开`时间轴`面板：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-a85386389e6ad1c75035ee7d276a5300.jpg)

接下来是“导入并处理”部分。目前有“帧动画”与“视频图层”两条路，具体哪一种更好我还不清楚，请练习后自行选择：

<br/>

**█ 导入并处理 方法一 “帧动画”**

菜单栏 -`文件`-`导入`-`视频帧到图层...`，找到并选中刚才导出的视频，单击`打开`：

（不要在这里多选文件，Ps 只会导入`文件名`处的第一个文件）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-b3a354c0b757166b1fe3cc6da9fa6f95.jpg)

此时会弹出`将视频导入图层`窗口：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-45177e38db6a962e4ce2e5b0bac3b372.jpg)

你可以在右侧滑块处调整欲导入视频素材的范围；

注意红框中的`制作帧动画`，请务必选中它；

注意橙框中的`限制为每隔 x 帧`（x 在 2 ~ 500 的范围内）。这个选项的作用是，是否按一定间隔抽取视频帧来导入 Ps，并丢弃剩下的帧，在这里我称它为“丢帧”。如果启用，那最终导入到 Ps 中的总帧数为：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-fb34a70c32428eac8d22638c7718baf6.jpg)

也就是说，剩下的帧都会被丢弃。这里有一个关于 x 值的演示：

（“Interval”即为 x 的值）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-9bc58b4ffc57083b7f5987b3007baff2.gif)

这里有一个最终效果的演示，只保留了 1/5 的帧（`限制为每隔 5 帧`），注意对比：

（这是 25FPS、100F 的 GIF）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-7924af1603178b72e582a291b75bbe8b.gif)

其实你可能会发现，丢弃 4/5 的帧也不太影响观感，所以你可以试着增加 x 的值，这样既能有效地加快 Ps 的处理速度、节省时间，又能降低最终生成的 GIF 动画文件的大小。

注意，如果你启用了“丢帧”，就一定记牢 x 的值，稍后会用到。

<br/>

完成设置后单击`确定`，此时可能会出现警告：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-bc937f67938eb4547053d6a90b98e457.jpg)

它们的含义是：

1. 最终导入到 Ps 中的总帧数超过了 300；
2. 最终导入到 Ps 中的总帧数超过了 500。

由于 Ps 并不是视频编辑软件，在处理动画上效率并不高，所以软件本身做了一些限制。要解决上述问题，你可以对素材进行剪辑（最好在 Ae 中处理），或者增加“丢帧”量（参考前文“`限制为每隔 x 帧`”内容），以减少最终导入 Ps 的帧的数量。

<br/>

导入素材后，要注意，Ps 会将当前帧动画的帧速率设定为导入素材的帧速率，如果之前进行了“丢帧”，那现在的动画就是“加速”过的（因为在按照原来的速度播放间隔较远的帧）。注意对比：

（这是 25FPS、250F 的 GIF）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-1b62cd272a80e41ba1e7cab14d4132e7.gif)

或者用上边那段素材做对比：

（这是 25FPS、100F 的 GIF）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-0bb0c2ac2d7dfb7aa5382263414f6541.gif)

为了恢复原速，需要进行如下操作：

单击`时间轴`面板右上角按钮调出菜单 -`选择全部帧`：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-da7555d659d39b5acc92fcc4c5bcfed9.jpg)

然后在任意一帧上单击那个持续时间（默认每帧时长） -`其它...`，打开`设置帧延迟`窗口：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-3730b040a5fc44c68f6a9e5d64d3e113.jpg)

这里你需要算出最终每帧应该持续多长时间：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-258a7deba726e3dadf9d9a13d1dc1488.jpg)

如果你在多次调整后忘记了“默认每帧时长”是多少，就找到你的视频素材，尝试计算：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-5be4bf744e1a8f797492aa66eaadf24a.jpg)

你还可以做其它的调整，更多内容请参阅：[创建帧动画](https://helpx.adobe.com/cn/photoshop/using/creating-frame-animations.html)

<br/>

**█ 导入并处理 方法二 “视频图层”**

菜单栏 -`文件`-`打开`（Ctrl+O），找到并选中刚才导出的视频，单击`打开`：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-15d8eaef2935db58f1a4e4467548b5d1.jpg)

你可以对这段素材进行更多的调整，右击`时间轴`面板-`视频组`中的图层，可以设置`速度`和`持续时间`：

（`速度`与`持续时间`是两码事，但在调整时可能会互相影响，不清楚会不会影响到帧率等等，要谨慎）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-64aa7d9df1df3e31be4865560ec44394.jpg)

更多内容请参阅：[编辑视频和动画图层](https://helpx.adobe.com/cn/photoshop/using/editing-video-animation-layers-photoshop.html)

<br/>

**█ 导出**

做好所有调整后，可以准备输出了。菜单栏 -`文件`-`导出`-`存储为 Web 所用格式（旧版）...`（Alt+Shift+Ctrl+S）：

（这个界面可能会很卡，所以操作不要太快，等等进度条）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-1acba783f80c50e1e4e143f4f82a8710.jpg)

`存储为 Web 所用格式`窗口中有一些比较关键的设置：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-1e34e68f5ce6e341b240e856da6d8a12.jpg)

* `颜色`一般选择 128 或 256，对比：

（在 0 损耗与 15 损耗下）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-4d2699a7ef51eccd9ef931e4ba6d94b5.jpg)

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-f2ba803575eda32e8ee1faca89de778b.jpg)

* 如果要输出有 Alpha 通道的 GIF，记得勾选`透明度`；
* 为了导出体积较小但质量还行的 GIF，可以适当调整`损耗`，在 10 ~ 20 之间都可以的，实验：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-80fd6fa615c17a1b0ef9890c2838391a.jpg)

* 通常，GIF 并不需要太高的分辨率，可以在`图像大小`处按需调整（只调整`百分比`可能会比较方便）；
* `动画`-`循环选项`，按需选择`一次`、`永远`或`其它...`；
* 其它的保持默认（有更好的建议请提出来）；

<br/>

最后，单击底部的`存储...`（不要点`完成`），选一个你能找到的文件夹和文件名保存文件。

如果出现以下警告，点`确定`就好：

（不建议你将 GIF 动画文件保存到存在包含[非拉丁字符](https://www.baidu.com/s?wd=%E9%9D%9E%E6%8B%89%E4%B8%81%E5%AD%97%E7%AC%A6)的路径）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-9e995dbfc6115cde8123d359b0abef0f.jpg)

<br/>

**█ 注意**

`存储为 Web 所用格式`窗口中三个按钮的作用：

* `存储...`是“输出文件并保存当前配置（以后可以一直用）再关闭窗口”；
* `完成`是“保存当前配置（同上）并关闭窗口”；
* `取消`是“放弃本次配置修改（如果有）并关闭窗口”。保存的配置（在 Windows 10 下的 Ps CC 2018）会被写入`%APPDATA%\Adobe\Adobe Photoshop CC 2018\Adobe Photoshop CC 2018 Settings\Save for Web Prefs.psp`，`%APPDATA%\Adobe\Adobe Photoshop CC 2018\Adobe Photoshop CC 2018\Recently Used Optimizations.irs`也会被修改。

有时，从`存储为 Web 所用格式`中导出并覆盖已有文件时，会发现旧文件并没有被覆盖，请参考文末“[异常处理](#%E5%BC%82%E5%B8%B8%E5%A4%84%E7%90%86)”以尝试解决这个问题。

<br/>

<br/>

# 用 AME 或 Pr 配合 Ae 导出 GIF

**█ 特征**

操作简单；

GIF 自动循环，无 Alpha 通道，画质一般。

<br/>

**█ 注意**

由于 AME 与 Pr 有类似的界面和操作流程，为了缩短文章长度，这一部分会将两款软件“合并”，请仔细阅读。

<br/>

**█ 首先**

保存你的 Ae 项目文件，或者将你的合成导出为 QuickTime 格式的视频。

<br/>

**█ 启动 AME 或 Pr 并导入文件**

* 你可以在 Ae 中选中你要导出的合成，然后菜单栏 -`文件`-`导出`-`添加到 Adobe Media Encoder 队列...`（Ctrl+Alt+M），这样能直接启动 AME 并导入当前 Ae 项目中的合成：

（以这种方式启动 AME 后，在 Ae 中修改打开的项目并不会影响 AME 中的项目，因为 AME 接收到的是当时的项目文件当时的副本）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-b10dc6b6cb9ceec1062db866bdf13c3f.jpg)

* 你也可以自行打开 AME，找到菜单栏 -`添加源`（Ctrl+I）；

* 或者，你打开 Pr 并新建一个项目，然后菜单栏 -`文件`-`导入`（Ctrl+I）；

接着找到刚才保存的 Ae 项目或导出的视频并选中它，单击`打开`：

（图是 Pr 的，AME 类似，下同）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-ea8789bcfbcfc5ae4c88bb599c827e15.jpg)

如果你导入了 Ae 项目文件，就要在弹出的`导入 After Effects 合成`窗口中找到你需要的合成，选中它，单击`确定`：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-b30c19019fe6a8018cd4b66ed5cd7e33.jpg)

<br/>

**█ （Pr 跳过）在 AME 中准备进行导出设置**

现在你可以在 AME 中看到一个条目，它的名称与你导入的视频文件/导入的 Ae 项目中的合成的名称相同，该条目叫作“源”；现在，这个“源”有一个子条目，它是叫作“输出”。

此时我的这个“输出”的设置是导出 H.264 编码的 mp4 文件，要进行调整——右击这个输出-`导出设置...`：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-2d493528940b13398368a54acc357e8f.jpg)

<br/>

**█ （AME 跳过）在 Pr 中处理素材并准备进行导出设置**

如果要改变刚导入素材的播放速度，或者为素材添加字符、调颜色等等，就右击素材-`从剪辑新建序列`以创建序列，再按照意愿进行编辑即可；

如果不需要对素材进行编辑，也可以不创建序列。

在“项目”面板中选中你要导出的素材或序列（仔细分辨哪一项是需要被导出的），菜单栏 -`导出`-`媒体`（Ctrl+M）：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-2077aa2a91c141f002c74ad4d1462a2b.jpg)

<br/>

**█ 进行导出设置**

将`格式`改为`动画 GIF`，**注意不是`GIF`**：

（图是 AME 的，Pr 类似，下同）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-5abcfb9712ac91173d4e025f4a899cd0.jpg)

单击`输出名称`后的链接，指定一个你找得到的路径和文件名，作为 GIF 文件的输出位置：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-ed46805de0091f6a925d2069500c70a2.jpg)

通常，GIF 并不需要太高的分辨率和帧率，你可以在导出前进行设置（这不影响素材或者 Ae 中的原合成）。将`基本视频设置`区域中`宽度`、`高度`后的勾去掉，并将他俩的值改小（参考左侧的预览框，按需、按比例调整）；再将`帧速率`后的勾去掉，并为其指定一个更低的值（10 ~ 15）：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-8bf2a32022b03d568fdf6f5a08553a82.jpg)

<br/>

**█ （Pr 跳过）从 AME 中导出**

完成设置后，单击`确定`返回 AME 主界面。

确保刚才你调整的这个输出的状态是`就绪`的，接着点绿色的`►（启动队列）`按钮，开始导出 GIF：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-558a9d86f3687a998ae03bd839013f38.jpg)

<br/>

**█ （AME 跳过）从 Pr 中导出**

完成设置后，单击`导出`（因为窗口焦点的原因，不要直接敲回车，否则会尝试启动 AME）。

<br/>

**█ 注意**

在“启动 AME 或 Pr 并导入文件”这一步导入 Ae 项目文件时，如果`导入 After Effects 合成`窗口中出现`无法打开项目`的提示，则说明 Ae 项目文件的版本高于 AME 或 Pr 的版本，无法完成导入：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-a7c5a130e8eeef81e8885fae739b1a85.jpg)

请参考文末“[异常处理](#%E5%BC%82%E5%B8%B8%E5%A4%84%E7%90%86)”以尝试解决这个问题。

<br/>

<br/>

# Ps 与 AME 或 Pr 导出文件的效果对比

经测试，AME 与 Pr 导出的 GIF 效果几乎没有差别，所以就只用 AME 和 Ps 的来比较了。

源视频信息：
```
*Suffix       : .mov
Codec ID/Info : CineForm High-Definition (HD) wavelet codec
*Frame Count  : 96
Bit rate      : 98.4 Mb/s
*Width:Height : 1920 : 1080 pixels [16:9]
Frame rate    : 25.000 FPS [Constant]
Color space   : YUV
Scan type     : Progressive
```
AME 导出配置：
```
Quality      : 100
Width:Height : 1920:1080 / 960:540 / 480:270
Frame Rate   : 25
Field Order  : Progressive
Aspect Ratio : 1.0
```
Ps 导出配置：

（下边的各个项目都是`存储为 Web 所用格式`窗口中的选项，可以参考[说明 1（原链接已失效）](https://web.archive.org/web/20171016220446/http://help.adobe.com/en_US/creativesuite/cs/using/WS6E857477-27FE-4a88-B8A4-074DC3C65F68.html#WS9E2C7F1A-87C0-4dae-9C0C-0C2B3C566F84)、[说明 2（原链接已失效）](https://web.archive.org/web/20171019152617/http://help.adobe.com/en_US/creativesuite/cs/using/WSC7A1F924-DD38-49b4-B84B-EFF50416C860.html#WSE07483CE-5D9F-4764-AA48-9DF708AD8479)、[类似功能在 Adobe Animate 中的说明](https://helpx.adobe.com/cn/animate/using/optimization-options-for-images-and-animated-gifs.html#GIFandPNG8optimizationoptions)）
```
优化
 | - 减低颜色深度算法 : 可选择
 | - 颜色            : 256
 | - 仿色算法        : 扩散
 | - 仿色            : 100%
 | - 透明度          : True
 | - 杂边            : #FFFFFF
 | - 透明度仿色       : 无透明度仿色
 | - 数量            : Disable
 | - 交错            : False
 | - Web靠色         : 0%
 | - 损耗            : 0% / 15%
 
颜色表
 | - 转换为sRGB      : True
 | - 预览            : 显示器颜色
 | - 元数据          : 版权和联系信息
 
图像大小
 | - W:H             : 1920:1080 / 960:540 / 480:270
 | - 品质            : 两次立方
```
<br/>

对比：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-114e93a3bd4c66c720ce94ca07614244.jpg)

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-0e69b787a4397dcd703acd5bde09c9ca.jpg)

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-0c7dda9e7a296c4799ae58283c3cfd9e.jpg)

<br/>

结论：

想要文件在保证质量的情况下尽量小（例如知乎限制图片大小不得超过 5 MB）：
```
使用 Ps，128/256 色，15 损耗，较低分辨率
```
最方便而且质量还不错：
```
使用 AME 或 Pr，100 Quality，完整分辨率

* 要注意 AME 或 Pr 貌似会影响动画的“速度”，进而影响到总时长。
```

----

# 用 Ae 脚本导出 GIF（仅介绍）

* GifGun

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-c910da30605361ebfccd27f695266eee.jpg)

官方介绍页：[https://aescripts.com/gifgun/](https://aescripts.com/gifgun/)

相关教程：

1. [AE脚本插件《gifGun》的安装使用教程以及错误提示的解决-UI中国-专业用户体验设计平台](https://www.ui.cn/detail/158270.html)

2. [AE CC2017直接导GIF插件—GifGun_1.5.1-UI中国-专业用户体验设计平台](https://www.ui.cn/detail/271758.html)

3. [Mac版本AE CC 2018脚本插件GIF GUN分享-UI中国-专业用户体验设计平台](https://www.ui.cn/detail/297944.html)

4. [用AE轻松输出GIF动图脚本-带详细安装教程-UI中国-专业用户体验设计平台](https://www.ui.cn/detail/159691.html)

可能会出现的问题（暂无解决方法，可能是不支持某些 Windows 7 或者低于 CS5 的 Ae？）：[gifgun插件安装不了，每次安装都会出现这个对话，求解。。。\_百度知道](https://zhidao.baidu.com/question/1370828323868744179.html)

<br/>

* Gif Magick

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-a40036d08e1fbbda425288ee498a9b30.jpg)

官方介绍页：[https://videohive.net/item/gif-magick-after-effects-script/14032323](https://videohive.net/item/gif-magick-after-effects-script/14032323)

相关教程：

1. [教你轻松AE导出GIF 内含安装包-UI中国-专业用户体验设计平台](https://www.ui.cn/detail/188372.html)

2. [用AE轻松输出GIF动图脚本-带详细安装教程-UI中国-专业用户体验设计平台](https://www.ui.cn/detail/159691.html)

<br/>

* aw_PreviewGenerator

（下边这个动图来自 aw_PreviewGenerator 的作者，[原图链接](https://camo.envatousercontent.com/fa824a1522c64c0a31e751694b046f4a6c3b4045/687474703a2f2f7370796c6162732e6f72672f686976652f70672f6465736372697074696f6e2f696d6167655f305f302e676966)）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-d83be0899a190e6ff2d40f10ea2589c2.gif)

官方介绍页：[https://videohive.net/item/aw_previewgenerator-after-effects-script/14081377](https://videohive.net/item/aw_previewgenerator-after-effects-script/14081377)

暂无相关教程。

----

# 异常处理

* 如果你在`存储为 Web 所用格式`导出时选择覆盖现有文件，但导出结束后文件没有发生变化，也没有任何提示，这就表明旧文件可能被占用了（我这边比较常见的是在 QQ 中以图片形式发送文件后会继续被 QQ 相关进程占用）。你可以尝试重新启动计算机来解决这个问题；

* 在不同版本的 Ae、Ps、AME 和 Pr 间进行一些操作（例如互相调用项目文件等）可能会因兼容性问题而失败，你可以尝试使用其它的媒介（例如 PNG 序列帧、QuickTime 格式的视频等）来手动完成操作。

# 注意事项

* QuickTime 格式的支持 Alpha 通道（透明度信息）的编解码器有这些：
```
DNxHR/DNxHD	// 不推荐使用 - 需要额外的复杂的设置
GoPro CineForm	// 推荐使用 - 默认 Quality = 4 即可
动画（Animation）// 没有 GoPro CineForm 就用这个
无（None）	// 不推荐使用 - 浪费磁盘空间

// 以下的都是安装 QuickTime 后新增的，依然建议用 GoPro CineForm
JPEG 2000, PNG, Planar RGB, TGA, TIFF 
```
![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-17500d563567c06a58b094c9a991e584.jpg)

* Ps 的`导入`-`视频帧到图层`的那个`限制为每隔 x 帧`，中文翻译并不准确，[英文原文](https://helpx.adobe.com/photoshop/how-to/make-animated-gif.html#optional__import_a_video)是“Limit To Every x Frames”，也就是“每 x 帧取一帧”，这就很明白了，同时也表明了为何会有大于等于 2 这个限制：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-77190cbc0ed214de27689dd592cdc2f7.jpg)

* 如果你要使用序列帧取代 QuickTime 视频文件作为应用之间传递的文件，就别用“psd 序列”制作带 Alpha 的 GIF，因为这依然会丢失 Alpha 通道的信息（我不清楚原因）；
* 如果你需要将 GIF 动画文件置于 Web 服务器、FTP 服务器等位置，或者需要将 GIF 动画文件嵌入各平台应用程序内，请确认你的文件能够被相关程序逻辑正确地处理；
* 本文中给出的各种方法都指向“从 Ae 导出 GIF”这个目标，忽略了一路上大量其它的详细设置，所以需要你自己去查找、学习。首先你需要 Adobe 官方的用户指南，以 Ae 为例，在菜单栏 -“帮助”-“After Effects 帮助...”（F1），在打开的网页里单击“用户指南”，开始学习：

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-afdd380aef793fb79156d38c36a8f68e.jpg)

# 未解决的问题

* Ps 中`时间轴`面板的`优化动画`选项有何用？[https://helpx.adobe.com/cn/photoshop/using/saving-exporting-video-animations.html#optimize_animation_frames](https://helpx.adobe.com/cn/photoshop/using/saving-exporting-video-animations.html#optimize_animation_frames)
* [photoshop中帧动画和时间轴的区别](https://zhidao.baidu.com/question/571446763.html)
* AME 或 Pr 对于动画“速度”的影响；
* AME 或 Pr 一定无法导出带 Alpha 的 GIF 了？
* Ae 导出 RGBA 的 psd 序列，但在 Ps 里打开看到背景是有颜色的（Pr、Ae 打开是有 Alpha 的），经测试，psd 中的背景色是 Ae 合成的“合成背景色”，为何：（相关问题：[https://www.zhihu.com/question/62864730](https://www.zhihu.com/question/62864730)）

![](https://raw.githubusercontent.com/pzhlkj6612/ZhihuPost-31567795/master/pic_zhimg_com/v2-fc2e00118edb2c706425c6c381c5442a.jpg)

* [Ae的GifGun插件怎么才能导出透明背景的gif？ - 知乎](https://www.zhihu.com/question/55557663)
* Ps 的`文件 File`-`导入 Import`-`视频帧到图层... Video Frames to Layers`，为何一直没在 helpx 上看到？？？
* Aep -> AME 或 Pr 直接导会生成副本嘛？
* AME 或 Pr 导出时设置的质量（Quality）与文件最终质量和大小的关系

----

# 推荐

* GIF 压缩：[GIF Compressor](https://gifcompressor.com/)
* 在线制作 GIF 的工具：[小猪动图](https://www.piggif.com/tools/video)
* Animated PNG(APNG)相关：[\[转载\]《再回眸，丽影如初》](https://www.uisdc.com/introduction-of-apng-gif)
* 是“渲染”还是“导出”：[在 After Effects CC 中进行渲染和导出的基础知识](https://helpx.adobe.com/cn/after-effects/using/basics-rendering-exporting.html)
* 关于 Ae 的渲染：[AE 渲染加速的一些方法](https://zhuanlan.zhihu.com/p/33730310)
* 知乎 & Markdown：[知乎编辑器，支持文档导入功能啦](https://zhuanlan.zhihu.com/p/33722618)

----

# 结尾

* 待更新的

Ps 导入视频素材方法二选一；

Ps->GIF 其中的内容需要被研究并修正（视频图层 时间轴动画 帧动画）；

Ps 视频图层“速度”与“持续时间”的关系，以及对帧率是否有影响；

`将视频导入图层`窗口不选中`制作帧动画`，如何继续制作帧动画；

[Adobe Generator 4 GIF](https://helpx.adobe.com/cn/photoshop/kb/save_for_web_Photoshop_CC_2015.html#whats-changing)；

Ps->GIF，Resize 的时机对于最终质量的影响；

Ps 视频图层-[`解释素材`](https://helpx.adobe.com/photoshop/using/importing-video-files-image-sequences.html#interpreting_video_footage)；

<br/>

* 参考

[After Effects CC (CS7) - Adobe Community](https://forums.adobe.com/thread/1236678)

[Making Animated GIFs From After Effects Comps](https://www.rocketstock.com/blog/making-animated-gifs-from-after-effects-comps/)

[animation - How to export a GIF from After Effects- - Graphic Design Stack Exchange](https://graphicdesign.stackexchange.com/questions/91994/how-to-export-a-gif-from-after-effects)

[VIDEO COPILOT - Export Animated GIF in After effects](http://www.videocopilot.net/forum/viewtopic.php?t=58672)

[【展哥】如何制作GIF动图（初级） - 【After Effects教程】干货实用AE实例教程合集【doyoudo出品】(6)\_野生技术协会\_科技\_bilibili\_哔哩哔哩](https://www.bilibili.com/video/av4612737/index_20.html#page=6)

[【中级】和我一起学AE 10\_野生技术协会\_科技\_bilibili\_哔哩哔哩](https://www.bilibili.com/video/av11696223/)

[[MG动画教程]财神循环动画制作\_野生技术协会\_科技\_bilibili\_哔哩哔哩](https://www.bilibili.com/video/av3732099/)

[GIF格式动画到底是怎么做出来的 - 知乎](https://zhuanlan.zhihu.com/p/23105036)

<br/>

[How to make an animated GIF in Photoshop | Adobe Photoshop CC tutorials](https://helpx.adobe.com/photoshop/how-to/make-animated-gif.html)

<br/>

[Photoshop CC 2015 中的“存储为 Web 所用格式”功能](https://helpx.adobe.com/cn/photoshop/kb/save_for_web_Photoshop_CC_2015.html#whats-changing)

[Creative Suite * 优化图像](https://help.adobe.com/zh_CN/creativesuite/cs/using/WS6E857477-27FE-4a88-B8A4-074DC3C65F68.html#WS9E2C7F1A-87C0-4dae-9C0C-0C2B3C566F84)

[GIF 和 PNG-8 优化选项 - Creative Suite * Web 图形优化选项](https://help.adobe.com/zh_CN/creativesuite/cs/using/WSC7A1F924-DD38-49b4-B84B-EFF50416C860.html#WSE07483CE-5D9F-4764-AA48-9DF708AD8479)

<br/>

[How can I export a transparent .gif-：AfterEffects](https://www.reddit.com/r/AfterEffects/comments/2x0sg1/how_can_i_export_a_transparent_gif/)

[transparency - Can I create a transparent GIF with After Effects- - Graphic Design Stack Exchange](https://graphicdesign.stackexchange.com/questions/94051/can-i-create-a-transparent-gif-with-after-effects/)

[Ae怎么导出透明背景视频？ - 范鹏的回答 - 知乎](https://www.zhihu.com/question/26993675/answer/89595667)

[有哪些软件可以将一段视频在尽量保证原视频质量的情况下转成gif动图？ - 知乎](https://www.zhihu.com/question/20757401)

<br/>

----

原回答：

[@徐勇智](https://www.zhihu.com/people/53fdf1ae511ba1280c742c5f949cbd4d) 关于“Ps 导入序列帧时帧速率设置”的指正；

[@吃生葱会流鼻血吗](https://www.zhihu.com/people/411f6a8f47dc572f8387c3fb7bdc55b3) 关于“Ps 导入序列帧方法”的提示；

<br/>

本文章：

[@幼麟](https://www.zhihu.com/people/ce7fa34ae305a5bfc099680e656e0246) 协助测试 Aep 兼容性。

[@呆槑](https://www.zhihu.com/people/95965bf3751fd054488859cc531533a8) 、[@MGWeysong](https://www.zhihu.com/people/340e2f329dada7c984bdf350f05f816d) 、[@幼麟](https://www.zhihu.com/people/ce7fa34ae305a5bfc099680e656e0246) 、[@栗子](https://www.zhihu.com/people/651b69fa91d4e3f51f2d5a3ad1c5d994) 、[@徐勇智](https://www.zhihu.com/people/53fdf1ae511ba1280c742c5f949cbd4d) 、[@佘朝光](https://www.zhihu.com/people/b02e779bbc76647a26a7472cb6247fb4) 提供了全文检查；

[@Sakura286](https://www.zhihu.com/people/b8da5ae8dc4346ae7ec0c88913a67cdf) 提供了 Ae CS4 的截图以及全文检查。

<br/>

[@墨子 2200MHz](https://www.zhihu.com/people/faf758840a7dfc528c4f620cdddf1460) 测试、整理。

<br/>

原答案发布于：2017.05.11

原答案修改于：2017.11.30

<br/>

修改于：17:41 2019/01/29

禁止转载。
