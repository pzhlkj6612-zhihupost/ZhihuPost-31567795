![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-b77e62f2328e988eb1606cabad155977.jpg)

禁止转载。

禁止转载是指“禁止转载本文内容”，可以通过超链接的方式分享本文。

<br/>

本文章内容由我在该问题下的回答处理而来：

[//www.zhihu.com/question/58159898/answer/167682476](//www.zhihu.com/question/58159898/answer/167682476)

本文章也存在于GitHub仓库：

[//github.com/pzhlkj6612/ZhihuPaper-31567795](//github.com/pzhlkj6612/ZhihuPaper-31567795)

<br/>

注意：

* 本文可能不会持续更新；
* 我仅在`Windows 7/10`下对本文内容做了简要测试；
* 我仅在`Adobe CS4/CC2017/CC2018`下对本文内容做了简要测试；
* 所有方法均由我从各个地方习得并测试，仅供参考，并不一定是最佳选择；
* 有问题请及时指出。

----

# 目录

* 概述
* 直接导出GIF（Ae CS5之前）
* 用Adobe家其它软件辅助Ae导出GIF
* 用Ae脚本导出GIF（仅介绍）
* 异常处理
* 注意事项
* 未解决的问题
* 推荐
* 结尾

----

# 概述

制作GIF动画的方法很多，本文只讨论从Ae开始，如何实现GIF动画的导出。

在当前最新版本软件中，从最终结果来看，以下路径是质量较高且过程简易的：

```
Ae合成 -<QuickTime(GoPro CineForm)>→ .mov视频文件 →

.mov视频文件 -<“视频帧到图层”>→ Ps帧动画 →

Ps帧动画 -<“存储为Web所用格式”>→ .gif动画文件
```

<br/>

文中用到的视频素材来自：《[【大花豹】极乐净土](//www.bilibili.com/video/av10397269/)》《[50帧又何妨（25FPS已重传）](//www.bilibili.com/video/av9198307/)》

----

# 直接导出GIF（Ae CS5之前）

早于Creative Suite 5([CS5(10.0)](//en.wikipedia.org/wiki/Adobe_After_Effects#History))版本的Ae支持导出GIF动画（[官方文档](//helpx.adobe.com/cn/after-effects/kb/supported-file-formats-effects-cs4.html#main__Supported_video_and_animation_file_formats_)）；
在这里我用Ae CS4(9.0.1)。

**█ 操作**

首先准备好你已制作完成的合成，然后菜单栏 -`图像合成`-`添加到渲染队列`（Ctrl+Shift+/）：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-43a1fa4812a7f682c5ff8bbd5ca63190.jpg)

找到刚才添加的合成，单击`输出组件`后的链接，打开`输出组件设置`窗口。在`基于“无损”`区域-`格式`选择`动画GIF`：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-b5c371feee1601b1a473f88e442fb7fd.jpg)

此时会弹出`动画GIF选项`窗口，按需调整，点`确定`：

（该窗口除了`循环`以外的设置的作用我还不清楚，保持默认即可）

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-d2dff1ebf23e3c3d09957360c8a1a041.jpg)

确定所有设置后，单击合成的`输出到：`后的链接，指定一个你找得到的路径和文件名，作为GIF文件的输出位置。完成一切操作后，单击`渲染队列`面板右侧的`渲染`，开始导出GIF：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-ed216ebc66f9840cd012237bc42a6dea.jpg)

**█ 注意**

通常，GIF并不需要太高的分辨率和帧率，你可以在导出前进行额外的设置（而不影响原合成）：

找到`渲染队列`面板中的合成，单击`渲染设置`后的链接，打开`渲染设置`窗口。`合成组名称`区域中的`分辨率`改为1/3、1/4等；再将`帧速率`区域中的`使用这个帧速率`选中，并为其指定一个更低的值（10~25）：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-8949ef58e69ffdb41f8e88a8c4077db0.jpg)

----

# 用Adobe家其它软件辅助Ae导出GIF

自CS5版本开始，Ae不再支持导出GIF动画了，现在`渲染队列`-`输出模块`打开`输出组件设置`，在`主要选项`-`格式`中找不到`动画GIF`：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-6da37738cd74d11773d91f70734d991c.jpg)

[Adobe官方的用户指南](//helpx.adobe.com/cn/after-effects/user-guide.html) > [渲染和导出](//helpx.adobe.com/cn/after-effects/user-guide.html?topic=/cn/zh-Hans/after-effects/morehelp/exporting_publishing_rendering.ug.js) > [渲染和导出基础知识](//helpx.adobe.com/cn/after-effects/using/basics-rendering-exporting.html) > [支持的输出格式](//helpx.adobe.com/cn/after-effects/using/basics-rendering-exporting.html#supported_output_formats) 中提到：

> 要创建动画 GIF 格式的影片，请首先从 After Effects 渲染和导出 QuickTime 影片。然后，将 QuickTime 影片导入 Photoshop，并且将影片导出为动画 GIF。

这表示，我们需要其它软件（例如Ps）的帮助才能获得GIF。其实不光是“QuickTime影片”，通过其它的中介（例如序列帧）最终也能得到GIF，但为了避免内容变得杂乱，我有意去掉了与“序列帧”有关的内容，感兴趣的朋友可以自己作尝试。

以下是Ps、AME、Pr三款软件配合Ae导出GIF动画文件的方法。

<br/>

* Adobe Photoshop

**█ 特征**

画质好，可设定GIF循环次数，可保留Alpha通道（透明度信息）；

操作耗时较长，且以`视频帧`方式导入的素材会从第500帧后截断（这并不代表只能做出500帧长度的GIF动画）

*（Photoshop的整个逻辑我还没有完全弄明白，但目前已写出的内容是没有问题、经得起验证的）*

**█ 首先**

保存你的Ae项目文件，并将你的合成导出为QuickTime格式的视频（建议选用GoPro CineForm编码）：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-49bf6c1d1fab4c37f0acf938389d7f60.jpg)

如果你需要制作带Alpha通道的GIF，就先从Ae导出带Alpha通道的视频，再导入Ps中做处理。

导出Ae合成之前，单击`输出组件`后的链接，打开`输出组件设置`窗口。`主要选项`中，`格式`选择`QuickTime`，`视频输出`区域-`通道`选择`RGB+Alpha`（如果`RGB+Alpha`不可选，就需要切换到正确的编解码器，参考文末“注意事项”）：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-323514efb5034765077ebccbc448b4c7.jpg)

通常，GIF并不需要太高的帧率，你可以在导出前进行额外的设置（而不影响原合成）。找到`渲染队列`面板中的合成，单击`渲染设置`后的链接，打开`渲染设置`窗口。将`帧速率`区域中的`使用此帧速率`选中，并为其指定一个更低的值（10~25）：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-e5d634b270ce4e16e8c66dd401359885.jpg)

通常，GIF也并不需要太高的分辨率，但不建议在导入Ps前做处理，以下是对比：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-e221297f02e0cf6848789af4398681b4.jpg)

打开Ps，找到菜单栏 -`窗口`-`时间轴`以打开`时间轴`面板：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-a85386389e6ad1c75035ee7d276a5300.jpg)

接下来是“导入与处理”，目前有两条路，具体哪一种更好我还不清楚，请练习后自行选择：

**█ 导入并处理 方法一 “帧动画”**

菜单栏 -`文件`-`导入`-`视频帧到图层`，找到并选中刚才导出的视频，单击`打开`：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-b3a354c0b757166b1fe3cc6da9fa6f95.jpg)

此时会弹出`将视频导入图层`窗口：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-45177e38db6a962e4ce2e5b0bac3b372.jpg)

你可以在右侧滑块处调整欲导入视频素材的范围；

注意红框中的`制作帧动画`，请务必选中它；

注意橙框中的`限制为每隔 x 帧`，如果启用，代表会对素材进行抽帧，最终导入到Ps中的总帧数为：

$总帧数=\frac{1}{x}\times选取范围内素材帧数$

请记牢`x`的值，稍后会用到。

<br/>

完成设置后单击`确定`，此时可能会出现警告：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-bc937f67938eb4547053d6a90b98e457.jpg)

意思是：

1. 最终导入到Ps中的总帧数超过了300；

2. 最终导入到Ps中的总帧数超过了500。

由于Ps并不是视频编辑软件，在处理动画上效率并不高，所以软件本身做了一些限制。要解决上述问题，你可以对素材进行裁剪（最好在Ae中处理），或者增加“抽帧”量，以减少最终导入Ps的帧数量。

<br/>

导入素材后，要注意，Ps会将当前帧动画的帧速率设定为导入素材的帧速率，如果之前进行了“抽帧”，那现在的动画就是“加速”过的。为了恢复原速，需要进行如下操作：

单击`时间轴`面板右上角按钮调出菜单 -`选择全部帧`：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-da7555d659d39b5acc92fcc4c5bcfed9.jpg)

然后在任意一帧上单击那个持续时间-`其它...`，打开`设定帧延迟`窗口：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-3730b040a5fc44c68f6a9e5d64d3e113.jpg)

这里你需要算出最终每帧应该有多少时长：

$每帧时长=默认每帧时长\times x$

如果你在多次调整后忘记了“默认每帧时长”是多少，就找到你的视频素材，尝试计算：

$默认每帧时长=\frac{1}{帧率}$

你还可以做其它的调整，更多内容请参阅：[创建帧动画](//helpx.adobe.com/cn/photoshop/using/creating-frame-animations.html)

**█ 导入并处理 方法二 “视频图层”**

菜单栏 -`文件`-`打开`（Ctrl+字母O），找到并选中刚才导出的视频，单击`打开`：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-15d8eaef2935db58f1a4e4467548b5d1.jpg)

你可以对这段素材进行更多的调整，右击`时间轴`面板-`视频组`中的图层，可以设置`速度`和`持续时间`：

（`速度`与`持续时间`是两码事，但在调整时可能会互相影响，不清楚会不会影响到帧率等等，要谨慎）

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-64aa7d9df1df3e31be4865560ec44394.jpg)

更多内容请参阅：[编辑视频和动画图层](//helpx.adobe.com/cn/photoshop/using/editing-video-animation-layers-photoshop.html)

**█ 导出**

做好所有调整后，可以准备输出了。菜单栏 -`文件`-`导出`-`存储为Web所用格式（旧版）...`：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-1acba783f80c50e1e4e143f4f82a8710.jpg)

（这个界面可能会很卡，操作不要太快，等等进度条）

`存储为Web所用格式`窗口中有一些比较关键的设置：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-1e34e68f5ce6e341b240e856da6d8a12.jpg)

* `颜色`一般选择128或256，对比：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-5467cd906e45a48d0b313986a85a074d.jpg)

* 如果要输出有Alpha通道的GIF，记得勾选`透明度`；
* 为了导出体积较小但质量还行的GIF，可以适当调整`损耗`，在10~20之间都可以的，实验：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-80fd6fa615c17a1b0ef9890c2838391a.jpg)

* 通常，GIF并不需要太高的分辨率，可以在`图像大小`处按需调整（只调整`百分比`可能会比较方便）；
* `动画`-`循环选项`，按需选择`一次`、`永远`或`其它...`；

其它的保持默认（有更好的建议请提出来）。

最后单击下边的`存储...`，选一个你能找到的文件夹和文件名保存文件。

如果出现以下警告，点`确定`就好：

（建议你不要将GIF动画文件保存到存在非拉丁字符的路径）

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-9e995dbfc6115cde8123d359b0abef0f.jpg)

<br/>

* Adobe Media Encoder/Premiere Pro

**█ 特征**

操作简单，GIF自动循环；

无Alpha通道；画质一般。

**█ 首先**

保存你的Ae项目文件，或者将你的合成导出为QuickTime格式的视频。

**█ 启动AME/Pr并导入文件**

你可以从Ae直接启动AME：在Ae中选中你要导出的合成，然后菜单栏 -`文件`-`导出`-`添加到Adobe Media Encoder 队列...`（Ctrl+Alt+M）：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-b10dc6b6cb9ceec1062db866bdf13c3f.jpg)

如果上述操作失败，或者你不愿意这么做，也可以：

（Pr跳过）打开AME，菜单栏 -`添加源`（Ctrl+大写字母I）；

（AME跳过）打开Pr，新建一个项目，接着菜单栏 -`文件`-`导入`（Ctrl+大写字母I），找到刚才保存的Ae项目或导出的视频并选中它，单击`打开`：

（图是Pr的，AME类似，下同）

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-ea8789bcfbcfc5ae4c88bb599c827e15.jpg)

如果你导入的是Ae项目文件，就要在弹出的`导入After Effects合成`窗口中找到你需要的合成，选中它，单击`确定`：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-b30c19019fe6a8018cd4b66ed5cd7e33.jpg)

**█ （Pr跳过）在AME中准备进行导出设置**

这个条目有着Ae的图标，名称与Ae中你选中合成的相同，该条目叫做“源”；现在，这个“源”有一个子条目，它是叫做“输出”。

此时我的这个“输出”的设置是导出H.264编码的mp4文件，要进行调整——右击这个输出-`导出设置...`：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-2d493528940b13398368a54acc357e8f.jpg)

**█ （AME跳过）在Pr中处理素材并准备进行导出设置**

如果要改变刚导入素材的播放速度，或者为素材添加字符、调颜色等等，就右击素材-`从剪辑新建序列`以创建序列，再按照意愿进行编辑即可；

如果不需要对素材进行编辑，也可以不创建序列。

在“项目”面板中选中你要导出的素材或序列（仔细分辨哪一项是需要被导出的），菜单栏 -`导出`-`媒体`（Ctrl+M）：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-2077aa2a91c141f002c74ad4d1462a2b.jpg)

**█ 进行导出设置**

将`格式`改为`动画GIF`，**注意不是`GIF`**：

（图是AME的，Pr类似，下同）

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-5abcfb9712ac91173d4e025f4a899cd0.jpg)

单击`输出名称`后的链接，指定一个你找得到的路径和文件名，作为GIF文件的输出位置：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-ed46805de0091f6a925d2069500c70a2.jpg)

通常，GIF并不需要太高的分辨率和帧率，你可以在导出前进行设置（而不影响素材或者Ae中的原合成）。将`基本视频设置`区域中`宽度`、`高度`后的勾去掉，并将他俩的值改小（参考左侧的预览框，按需、按比例调整）；再将`帧速率`后的勾去掉，并为其指定一个更低的值（10~15）：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-8bf2a32022b03d568fdf6f5a08553a82.jpg)

**█ （Pr跳过）从AME中导出**

完成设置后，单击`确定`返回AME主界面。

确保刚才你调整的这个输出的状态是`就绪`的，接着点绿色的`►（启动队列）`按钮，开始导出GIF：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-558a9d86f3687a998ae03bd839013f38.jpg)

**█ （AME跳过）从Pr中导出**

完成设置后，单击`导出`（别直接敲回车，不然会尝试启动AME）。

**█ 注意**

在“启动AME/Pr并导入文件”这一步导入Ae项目文件时，如果`导入After Effects合成`窗口中出现`无法打开项目`的提示，则说明Ae项目文件的版本高于AME/Pr的版本，无法完成导入：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-a7c5a130e8eeef81e8885fae739b1a85.jpg)

不过，也有解决这个问题的可能性，请参考文末“异常处理”xxxxxxxxxxx。

<br/>

* 相互比较

经测试，AME与Pr导出的GIF效果几乎没有差别，所以就只用AME和Ps的来比较了。
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

----

# 用Ae脚本导出GIF（仅介绍）

* GifGun

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-c910da30605361ebfccd27f695266eee.jpg)

官方介绍页：[//aescripts.com/gifgun/](//aescripts.com/gifgun/)

相关教程：[//www.ui.cn/detail/158270.html](//www.ui.cn/detail/158270.html)

可能会出现的问题（暂无解决方法，可能是不支持Win7？）：[//zhidao.baidu.com/question/1370828323868744179.html](//zhidao.baidu.com/question/1370828323868744179.html)

<br/>

* Gif Magick

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-a40036d08e1fbbda425288ee498a9b30.jpg)

官方介绍页：[//videohive.net/item/gif-magick-after-effects-script/14032323](//videohive.net/item/gif-magick-after-effects-script/14032323)

相关教程：[//www.ui.cn/detail/159691.html](//www.ui.cn/detail/159691.html)

<br/>

* aw_PreviewGenerator

官方介绍页：[//videohive.net/item/aw_previewgenerator-after-effects-script/14081377](//videohive.net/item/aw_previewgenerator-after-effects-script/14081377)

暂无相关教程。

<br/>

注意，本文暂不对以上三款Ae脚本作更多的说明。

----

# 异常处理

* 不同版本的Ae、Pr、Ps、AME间存在的兼容性问题会让许多操作陷入停顿，所以应该尝试将软件间传递的文件转换为兼容性更高的类型，例如GoPro CineForm编码、QuickTime格式的视频，或者PNG序列帧等等。

# 注意事项

* QuickTime格式的支持Alpha通道（透明度信息）的编解码器有这些：
```
DNxHR/DNxHD // 不推荐使用 - 需要额外的复杂的设置
GoPro CineForm // 推荐使用 - 默认 Quality=4 即可
动画（Animation） // 没有GoPro CineForm就用这个
无（None） // 不推荐使用 - 浪费磁盘空间

// 以下的都是安装QuickTime后新增的，依然建议用GoPro CineForm
JPEG 2000, PNG, Planar RGB, TGA, TIFF 
```
![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-17500d563567c06a58b094c9a991e584.jpg)

* 如果你要使用序列帧取代QuickTime视频文件作为应用之间传递的文件，别用psd序列制作带Alpha的GIF，因为这依然会丢失Alpha通道信息（我不清楚原因）；
* 如果你需要将GIF动画文件置于Web服务器、FTP服务器等位置，或者需要将GIF动画文件嵌入各平台应用程序内，请确认你的文件能够被相关程序逻辑正确地处理；
* 本文中给出的各种方法都指向“从Ae导出GIF”这个目标，忽略了一路上大量其它的详细设置，所以需要你自己去查找、学习。首先你需要Adobe官方的用户指南，以Ae为例，在菜单栏 -“帮助”-“After Effects帮助...”（F1），在打开的网页里单击“用户指南”，开始学习：

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-54025408ef9bdc3b480ed23ebdbcdad9.jpg)

# 未解决的问题

* Ps中`时间轴`面板的`优化动画`选项有何用？[//helpx.adobe.com/cn/photoshop/using/saving-exporting-video-animations.html#optimize_animation_frames](//helpx.adobe.com/cn/photoshop/using/saving-exporting-video-animations.html#optimize_animation_frames)
* [photoshop中帧动画和时间轴的区别](//zhidao.baidu.com/question/571446763.html)
* Pr/AME一定无法导出带Alpha的GIF了？
* Ae导出RGBA的psd序列，但在Ps里打开看到背景是有颜色的（Pr、Ae打开是有Alpha的的），经测试，psd中的背景色是Ae合成的“合成背景色”，为何：（相关问题：[//www.zhihu.com/question/62864730](//www.zhihu.com/question/62864730)）

![](https://github.com/pzhlkj6612/ZhihuPaper-31567795/blob/master/pic_zhimg_com/v2-fc2e00118edb2c706425c6c381c5442a.jpg)

----

# 推荐

* GIF压缩：[GIF Compressor](//gifcompressor.com/)
* 在线制作GIF的工具：[小猪动图](//www.piggif.com/tools/video)
* Animated PNG(APNG)相关：[[转载]《再回眸，丽影如初》](//www.uisdc.com/introduction-of-apng-gif)
* 是“渲染”还是“导出”：[在 After Effects CC 中进行渲染和导出的基础知识](//helpx.adobe.com/cn/after-effects/using/basics-rendering-exporting.html)
* 关于Ae的渲染：[AE 渲染加速的一些方法](//zhuanlan.zhihu.com/p/33730310)
* 知乎 & Markdown：[知乎编辑器，支持文档导入功能啦](//zhuanlan.zhihu.com/p/33722618)

----

# 结尾

* 待更新的

Ps导入视频素材方法二选一；

Ps->GIF其中的内容需要被研究并修正（视频图层 时间轴动画 帧动画）；

Ps视频图层“速度”与“持续时间”的关系，以及对帧率是否有影响；

`将视频导入图层`窗口不选中`制作帧动画`，如何继续制作帧动画。

<br/>

* 参考

[//forums.adobe.com/thread/1236678](//forums.adobe.com/thread/1236678)

[//www.rocketstock.com/blog/making-animated-gifs-from-after-effects-comps/](//www.rocketstock.com/blog/making-animated-gifs-from-after-effects-comps/)

[//graphicdesign.stackexchange.com/questions/91994/how-to-export-a-gif-from-after-effects](//graphicdesign.stackexchange.com/questions/91994/how-to-export-a-gif-from-after-effects)

[//www.videocopilot.net/forum/viewtopic.php?t=58672](//www.videocopilot.net/forum/viewtopic.php?t=58672)

[//www.bilibili.com/video/av4612737/index_20.html#page=6](//www.bilibili.com/video/av4612737/index_20.html#page=6)

[//www.bilibili.com/video/av11696223/](//www.bilibili.com/video/av11696223/)

[//www.bilibili.com/video/av3732099/](//www.bilibili.com/video/av3732099/)

[//zhuanlan.zhihu.com/p/23105036](//zhuanlan.zhihu.com/p/23105036)

<br/>

[//www.reddit.com/r/AfterEffects/comments/2x0sg1/how_can_i_export_a_transparent_gif/](//www.reddit.com/r/AfterEffects/comments/2x0sg1/how_can_i_export_a_transparent_gif/)

[//graphicdesign.stackexchange.com/questions/94051/can-i-create-a-transparent-gif-with-after-effects/](//graphicdesign.stackexchange.com/questions/94051/can-i-create-a-transparent-gif-with-after-effects/)

[//www.zhihu.com/question/26993675/answer/89595667](//www.zhihu.com/question/26993675/answer/89595667)

[//www.zhihu.com/question/20757401](//www.zhihu.com/question/20757401)

<br/>

* 感谢

[@徐勇智](//www.zhihu.com/people/53fdf1ae511ba1280c742c5f949cbd4d) 关于“Ps导入序列帧时帧速率设置”的指正；

[@吃生葱会流鼻血吗](//www.zhihu.com/people/411f6a8f47dc572f8387c3fb7bdc55b3) 关于“Ps导入序列帧方法”的提示；

[@陈璇](//www.zhihu.com/people/b8da5ae8dc4346ae7ec0c88913a67cdf) 提供了“Ae CS4”的截图；

[@horbyn4zZ](//www.zhihu.com/people/ce7fa34ae305a5bfc099680e656e0246) 协助测试Aep兼容性。

----

原答案发布于：2017.05.11

原答案修改于：2017.11.30

<br/>

修改于：25:64 2017/13/42

禁止转载。
