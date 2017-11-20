# X天小程序开发速度入门--第5天

> 苦海无涯，编程却有结束的那一天
> 如果从创业那天开始算，7年一辈子，在写下这段文字的时候，我的程序员生涯还有`5年 44天 3小时 21分 5秒`
> 该做的抓紧做，该学的抓紧学

今天把quick start项目里不清楚的`语法`都过一遍

## JavaScript
### 箭头函数
```
    wx.login({
      success: res => {
        // 发送 res.code 到后台换取 openId, sessionKey, unionId
      }
    })
```

这里面 `res => { }` 定义了一个匿名函数，ECMAScript 6支持这种写法，等同于

```
    wx.login({
      success: function(res)  {
        // 发送 res.code 到后台换取 openId, sessionKey, unionId
      }
    })
```

### 逻辑运算符 ||
```
var logs = wx.getStorageSync('logs') || []
```

1 在调试，Source面板下断点
2 在调试，Console面板下输入 `wx.getStorageSync('logs')`
    * 初次运行或者清除缓存后，会返回空数组
3 上面这句，在 `wx.getStorageSync('logs')` 返回 `undefined` 情况下，会返回一个空数组
    * `undefined`  在条件语句中判定为 `false`

**上面语句的含义**：返回 logs 非空数组（本地缓存），或者返回空数组

### 数组操作 unshift
```
  onLaunch: function () {
    // 展示本地存储能力
    var logs = wx.getStorageSync('logs') || []
    logs.unshift(Date.now())
    wx.setStorageSync('logs', logs)
```

* `unshift()`  方法可向数组的开头添加一个或更多元素，并返回新的长度
* 小程序初始化完成  `onLaunch` 事件发生，会记录当前日期到 logs 数组，存储到本地缓存

### this对象
```
wx.getUserInfo({
	success: res => {
		// 可以将 res 发送给后台解码出 unionId
		this.globalData.userInfo = res.userInfo

		// 由于 getUserInfo 是网络请求，可能会在 Page.onLoad 之后才返回
		// 所以此处加入 callback 以防止这种情况
		if (this.userInfoReadyCallback) {
			this.userInfoReadyCallback(res)
		}
```
`this` 对象不同场合有各种不同的用法，上面的代码中，`this` 代表的是Global对象
* 在微信IDE中 `CTRL+SHIFT+F` 查找 `userInfoReadyCallback`，可以看到 index.js 中定义了这个函数
* 这段代码的目的，就是为了防止 Page.onLoad 比  `onLaunch` 事件中请求的用户信息成功之前已运行，此时app.globalInfo.userInfo的值是空的，所以还需要再重新对其进行赋值

### 全局变量
```
  globalData: {
    userInfo: null
  }
```
app.js 里定义了 `globalData` 全局变量，于是在各个地方都用到了，进行用户信息传递

理论上有两种方法可以查看  `globalData`  被调用的情况
* 右键菜单，查找所有引用：恩，没有用
*  `CTRL+SHIFT+F` 查找  `globalData`：可以看到，在 app.js 和 index.js 中分别进行了赋值和使用

题外话：不得不说，IDE做得还是有很大提升空间

### console.log
```
  getUserInfo: function(e) {
    console.log(e)
```

这是很重要的调试技巧，上面的代码把 `UserInfo` 在Console面板中打印了出来

* Source面板下断点
* 执行 `console.log(e)` 或者 直接在Console面板下输入 `console.log(e)` 回车，都可以看到返回的用户信息 

注意：`UserInfo` 里面还有一些加密信息，这个坑待填 TODO

## 微信API
### wx.getSetting
```
    wx.getSetting({
      success: res => {
        if (res.authSetting['scope.userInfo']) {
```
* wx.getSetting 获取用户的当前设置：返回success，可以查看用户信息，完整信息参见 [scope 列表](https://mp.weixin.qq.com/debug/wxadoc/dev/api/authorize-index.html)

### setData
**此处应有许多坑**

> Page.prototype.setData()
> [官方说明](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/app-service/page.html)：setData 函数用于将数据从逻辑层发送到视图层（异步），同时改变对应的 this.data 的值（同步）

然后列举了一堆限制
* 直接修改 `this.data` 而不调用 `this.setData` 是无法改变页面的状态的，还会造成数据不一致。
* 单次设置的数据**不能超过1024kB**，请尽量避免一次设置过多的数据。
* 请不要把 `data` 中任何一项的 `value` 设为 `undefined` ，否则这一项将不被设置并可能遗留一些潜在问题

举例：index.js 中
```
this.setData({
	userInfo: app.globalData.userInfo,
	hasUserInfo: true
})
```

设置了 `userInfo` 和 `hasUserInfo` ，在 index.wxml 中使用
```
<!--index.wxml-->
<view class="container">
  <view class="userinfo">
    <button wx:if="{{!hasUserInfo && canIUse}}" open-type="getUserInfo" bindgetuserinfo="getUserInfo"> 获取头像昵称 </button>
    <block wx:else>
      <image bindtap="bindViewTap" class="userinfo-avatar" src="{{userInfo.avatarUrl}}" background-size="cover"></image>
      <text class="userinfo-nickname">{{userInfo.nickName}}</text>
    </block>
  </view>
  <view class="usermotto">
    <text class="user-motto">Hello {{userInfo.nickName}}</text>
  </view>
</view>
```

### Page
这个坑明天再填

## 总结
对照代码学习JavaScript思路
* 在W3C的离线教程里搜索 JavaScript + 关键字
* 如果找不到，在 GitHub 的[教程](https://github.com/zhubangbang/)里搜索
* 如果还是找不到，再百度 JavaScript + 关键字 或者 小程序 + 关键字

> 写完这篇，我的程序员生涯还剩下 5年 44天 2小时 4分 48秒
> 该做的抓紧做，该学的抓紧学