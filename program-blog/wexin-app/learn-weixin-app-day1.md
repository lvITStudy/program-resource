# X天小程序开发速度入门--第1天

* 小程序是什么？ 微信的应用号
* 小程序怎么开发？ 用微信开发工具
* 小程序用的什么语言？ 分前台与后台，前台是微信风格的app，后台是业务接口，可以用多种后台语言开发
* 开发小程序的过程是怎样的？ 从Hello World开始吧……

## 建立第一个小程序 Hello World
需求
* 登录小程序
* 显示用户信息
* 打印 "Hello小程序"

## 步骤
### 注册
1 注册微信小程序账号：https://mp.weixin.qq.com/
   * 立即注册->小程序
   * 填写注册信息，提交注册
2 注册好的账号登录小程序
3 下载开发者工具：[下载地址 ](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/download.html?t=1510576089)

### 准备步骤
1 打开 **微信web开发者工具**
   * 注意：微信开发工具变更很快，可能与网络书籍教程无法一一对应，需要自己多摸索。
2 选择**小程序项目**
   * 登录界面提供了 [微信开发者文档](https://mp.weixin.qq.com/debug/wxadoc/dev/index.html)
   * [微信开发者社区](https://developers.weixin.qq.com/home?token=137700584&lang=zh_CN)
3 点击**管理项目**左边的"加号 +**
4 填写项目名称**Hello小程序**，选择好项目目录
5 AppID先选择无，待申请注册通过后，可以填写自己小程序的AppID
6 勾选“创建QuickStart项目**：会创建项目基本结构

### 理解微信项目文件
> 破坏是学习的一种很好方式

* 删除目录下所有文件，点**编译**
   * 这时会看到报错"未找到入口 app.json 文件，或者文件读取失败，请检查后重新编译。"
   * 微信启动时会查找app.json入口文件
* 添加app.json
   * 继续报错"Expecting 'STRING','NUMBER','NULL','TRUE','FALSE','{','[', got EOF"
   * app.json必须符合json格式
* 添加 `{}`
   * 继续报错“未找到入口页面 app.json 中定义的 pages : []”
   * 说明必须添加页面 `pages : []`
* 添加页面
   * 目录导航上方"+"
      * 增加目录pages
      * 增加页面index
      * 修改"index.wxml"内容为`<text>Hello小程序</text>`
* 小程序模拟器显示预览输出 `Hello小程序`
