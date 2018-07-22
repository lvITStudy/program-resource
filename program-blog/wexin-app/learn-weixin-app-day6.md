# X天小程序开发速度入门--第6天
> 关于JavaScript语法，《JavaScript精粹》是一本经典参考书，可以随时查找和翻一翻
> 举例，数组 unshift 在这本书里就有专门的介绍
> 可以把每个章节过一遍，在 Console 面板里把示例运行一下

今天继续梳理 quick start 项目代码，在理解了项目 app.js 后，对页面的 JavaScript 进行梳理
* index.js
* log.js

## 页面结构
新建页面，比如 hello，会创建4个文件
* hello.js：JavaScript 脚本逻辑文件
    * 响应用户的点击、获取用户的位置等等
    * 支持绑定 WXML事件，可以绑定的事件参见 [事件系统](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/event.html)：注意，这里提到的事件都是**非冒泡事件**，关于 html DOM 的 事件冒泡机制(Event bubbling) 是一种事件传递机制，在w3c规范里有详细的描述，要彻底理解，可以参阅 [这里](https://www.w3.org/TR/2000/REC-DOM-Level-2-Events-20001113/events.html)
    * 绑定事件后，在事件响应中调用微信API处理业务，更新数据
* hello.json：JSON 配置文件 *非必须*
    * 设置 app.json 中的 window 配置项的内容，页面中配置项会覆盖 app.json 的 window 中相同的配置项
    * [页面json配置说明](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/config.html) 中的 **page.json**。主要包含导航栏标题内容、背景颜色、是否开启下拉刷新、下拉效果等
* hello.wxml：WXML 模板文件，类似 HTML 
    * 与标准的 HTML 不同，小程序提供了一组自己的[基础组件](https://mp.weixin.qq.com/debug/wxadoc/dev/component/)
    * 通过[事件系统](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/event.html)，提供界面响应，可以通过 `console.log(e)` 输出事件的详细信息。事件包含的内容(参数)也在[事件系统](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/event.html)中有详细的说明
    * [数据绑定](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/data.html) 对 Page 中 data 里定义的数据
        * `{{ }}` 的语法把一个变量绑定到界面，支持表达式等
    * [列表渲染](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/list.html)
        * `wx:for` 绑定数组，重复渲染
    * [条件渲染](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/conditional.html)
        * `wx:if` 判断是否需要渲染
    * [模板](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/template.html)：定义模板，然后引用
        * 采用了 [mustache.js](https://github.com/janl/mustache.js) ：[支持多种语言的无逻辑(logic-less)模板库](http://mustache.github.io/)
    * 事件
    * [引用](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/import.html)
        * `import`：导入模板，这里有**作用域**的问题
        * `include`：相当于直接拷贝到这里
* hello.wxss：WXSS 样式文件
    * 针对微信的[样式](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxss.html)：可类比CSS
    * 支持样式导入和内联样式
    * 在 app.wxss 定义全局样式，在 page.wxss 定义页面局部样式，会覆盖全局样式

这4个文件必须命名相同，在整个项目的配置文件 app.json 中，会根据 `pages` 的配置自动找到对应的资源
```
  "pages": [
    "pages/index/index",
    "pages/logs/logs",
    "pages/index/hello"
  ],
```

## 举例，wxss, js, wxml 如何工作
`index` 页面，显示欢迎信息，点击"获取头像昵称"请求用户信息

### 页面结构
index.wxml 去掉样式
```
<!--index.wxml-->
<view>
  <view>
    <button wx:if="{{!hasUserInfo && canIUse}}" open-type="getUserInfo" bindgetuserinfo="getUserInfo"> 获取头像昵称 </button>
    <block wx:else>
      <image bindtap="bindViewTap" src="{{userInfo.avatarUrl}}"></image>
      <text>{{userInfo.nickName}}</text>
    </block>
  </view>
  <view>
    <text>Hello {{userInfo.nickName}}</text>
  </view>
</view>
```

* 页面结构：view(view(button, block(image, text)), view(text))
* 事件处理：
    * 点击按钮事件：`bindgetuserinfo`
    * 点击头像图片事件：`bindtap`
* 数据绑定：
    * `{{userInfo.avatarUrl}}`：用户头像
    * `{{userInfo.nickName}}`：用户名
    * `Hello {{userInfo.nickName}}`：欢迎信息
* 条件渲染：
    * `wx:if="{{!hasUserInfo && canIUse}}"`：没有用户信息，显示**获取用户头像信息**按钮
    * `<block wx:else>`：如果已登录，显示用户头像及姓名

### 脚本逻辑
```
Page({
  data: {
    motto: 'Hello World',
    userInfo: {},
    hasUserInfo: false,
    canIUse: wx.canIUse('button.open-type.getUserInfo')
  },
```

定义了 index 页面数据：包括标题 `motto`，用户信息 `userInfo`，是否已登录 ` hasUserInfo`，判断**基础库是否可以使用 `getUserInfo` API**，确保[兼容性](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/compatibility.html)

```
wxml
<image bindtap="bindViewTap" src="{{userInfo.avatarUrl}}"></image>

js
  bindViewTap: function() {
    wx.navigateTo({
      url: '../logs/logs'
    })
  },
```

事件处理，点击用户头像后调用 `wx.navigateTo` 跳转到日志页面

```
wxml
    <button wx:if="{{!hasUserInfo && canIUse}}" open-type="getUserInfo" bindgetuserinfo="getUserInfo"> 获取头像昵称 </button>

js
  getUserInfo: function(e) {
    console.log(e)
    app.globalData.userInfo = e.detail.userInfo
    this.setData({
      userInfo: e.detail.userInfo,
      hasUserInfo: true
    })
  }
```

点击按钮，`open-type="getUserInfo'` 获取用户信息， `bindgetuserinfo` 回调函数提供获取到的用户信息
参见[表单组件 button](https://mp.weixin.qq.com/debug/wxadoc/dev/component/button.html)

### 样式文件
```
.wxml
<view class="userinfo">

.wxss
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}
```

定义了页面中的各组件样式，通过 `class` 筛选器渲染

当然，也可以使用 css 中的属性，比如 `background-size`

## JavaScript
log.js
```
logs: (wx.getStorageSync('logs') || []).map(log => {
	return util.formatTime(new Date(log))
})
```

上面的代码返回数组后，调用了 [Array.prototype.map()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/map)，对所有的日志进行了格式化

```
const util = require('../../utils/util.js')

util.formatTime(new Date(log))
```

引入 util.js 对日期进行格式化 

```
const formatTime = date => {
  const year = date.getFullYear()
  const month = date.getMonth() + 1
  const day = date.getDate()
  const hour = date.getHours()
  const minute = date.getMinutes()
  const second = date.getSeconds()

  return [year, month, day].map(formatNumber).join('/') + ' ' + [hour, minute, second].map(formatNumber).join(':')
}
```

`date.getMonth() ` 返回值是 0（一月） 到 11（十二月） 之间的一个整数，所以上面的代码做了加1

```
const formatNumber = n => {
  n = n.toString()
  return n[1] ? n : '0' + n
}
```

把数字进行补0处理，先转为字符串，然后判断是否两位 `n[1] `如果为 true，直接返回，否则补0

```
module.exports = {
  formatTime: formatTime

```

将一些公共的代码抽离成为一个单独的 js 文件，作为一个模块。模块只有通过 module.exports 或者 exports 才能对外暴露接口
参见[模块化](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/app-service/module.html)，[JavaScript export语句](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)

## 总结
* 如何有效地找到一个技术的基本规范：中文描述，百度搜索归属的技术，查找对应的英文翻译，找维基百科，查看参考文献，定位标准。
    * 举例，JavaScript 冒泡事件，搜索归属于 HTML DOM事件流，查找 event bubble/propagation，定位 W3C 规范
* 在小程序文档分类栏目  **简易教程  框架  组件  API  工具  Q&A** 的最右边有搜索框，可以直接搜索想要的内容，在[MDN](https://developer.mozilla.org/en-US/)同样有效

