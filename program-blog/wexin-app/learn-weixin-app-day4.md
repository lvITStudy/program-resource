# X天小程序开发速度入门--第4天

感冒休息了1天，今天继续

> 熟悉[小程序开发工具](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/devtools.html)

## 解决以下问题
* 项目常见操作：新建无AppID项目、删除项目、打开/切换项目、查看项目信息
    * 导入：**目前没有提供导入项目功能，早期版本有过**，可采取暴力文件删除拷贝方式
    * 查看项目信息：点“详情”
    * **设置项目基础库**：点“详情”，工具基础库版本，用来调试低版本兼容
* 项目文件、目录操作
    * 1.0.1171160版本解决了在目录下创建目录和文件问题，新增了**Component**
* 编辑文件：设置背景色、字体
    * 自动提示：对微信API做了很好的提示，JavaScript、JSON、WXML都做了很好的提示，用`TAB`键补全
* 调试：这是很关键的一个功能
    * 调试器 Console：输入和调试代码，比起在debug里面查看变量方便很多
    * 调试器 Wxml：可以直接查看wxml 转化后的界面，与chrome里面查看html的DOM模型一样
    * 调试器 Source：查看源码，下断点，调试
    * 调试器 AppData：查看数据非常方便，比如定义的userInfo、motto等信息
    * 调试器 Storage：查看本地存储，配合清缓存调试
    * 调试器 Network：查看网络调用，与后台通信时用到
    * 调试器 Sensor：模拟地理位置和重力感应，高级功能（不大常用:P）

##  其他重要功能
* 切后台：模拟小程序切换到后台的状态
* 预览：在手机上预览，需要AppID
* 上传、测试、腾讯云
    * 点“详情”，域名信息：做设置

## 其他功能
* 点工具登录头像：可以查看版本更新信息，以及在社区文章中的回复

工具已OK，可以上路了。

## 注意事项
* 一些微信API必须在真机实验，参见[这里](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/notsupport.html)
* 一些JavaScript API不支持，参见[这里](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/details.html#客户端es6-api-支持情况)
* 工具要每天更新，切记