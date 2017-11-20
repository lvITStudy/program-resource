# X天小程序开发速度入门--第3天

> 继续昨天的学习，今天读了
> * [简易教程](https://mp.weixin.qq.com/debug/wxadoc/dev/)
> * [框架](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/MINA.html)
> * [基础组件](https://mp.weixin.qq.com/debug/wxadoc/dev/component/)
> * [API](https://mp.weixin.qq.com/debug/wxadoc/dev/api/)
> * [工具](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/devtools.html)
> * [Q&A](https://mp.weixin.qq.com/debug/wxadoc/dev/qa.html)
> * [开发者社区](https://developers.weixin.qq.com/)

虽然很着急马上动手写码，但以前的经验告诉我，冷静，先看好文档。

道理很简单，了解需要的资源在哪里，什么能读懂，什么看不懂，才能有针对性的实验和学习。

##  [简易教程](https://mp.weixin.qq.com/debug/wxadoc/dev/)
与其在网上东找西凑，不如到官网花点时间好好读读，入门教程：
* 基础
    * 起步
        * 申请帐号
        * 安装开发工具：官方的[工具文档](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/devtools.html)必须好好读一下，然后操练
        * 我的第一个小程序
        * 编译预览
    * 代码构成
        * JSON 配置：[app.json配置](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/config.html) *官网文档给的链接过期，看来bug不少*
        * WXML 模板：[WXML标签语言](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/) *微信自定义标签语言，运行在webview下，定制的 html*。微信提供了[一套组件](https://mp.weixin.qq.com/debug/wxadoc/dev/component/)，熟练掌握组件，在处理需求时可以灵活运用
        * WXSS 样式：[WXSS样式表](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxss.html) *微信自定义样式语言，阉割版的 css，使用时有许多限制*。配合 [WXS脚本](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxs/) 构建页面结构
        * JS 逻辑交互：通过 [事件](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/event.html) 响应用户行为。微信提供了一套 [API](https://mp.weixin.qq.com/debug/wxadoc/dev/api/)，熟练掌握用法、限制以及各种坑，很关键
    * 小程序能力
        * 小程序的启动：需要了解小程序的生命周期，包括隐藏、唤醒、销毁、冷启动/热启动
        * 程序与页面：需要了解页面的生命周期，页面跳转，页面栈在各种状态下的处理
        * 组件
        * API
    * 发布前的准备
        * 用户身份
        * 预览
        * 上传代码
        * 小程序的版本：这里需要关注 [基础库](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/client-lib.html)的版本，对于向下版本的兼容，是很大的一个坑
    * 上线：看了 [开发者社区](https://developers.weixin.qq.com/) 未解决的问题，就知道微信的坑有多少
        * 提交审核
        * 发布
        * 运营数据
* 体验小程序
* 更新日志

看起来似乎正在按照教程的路线在走，接下来应该是要想好第一个版本小程序的内容，解决文档和demo中遇到的不理解的问题。

