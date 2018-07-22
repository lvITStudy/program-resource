# X天小程序开发速度入门--第2天
> 11月14日很自觉地学习，感觉那种拖延症的感觉轻了很多

继续 Quick Start 学习，今天主要的收获有：
* 微信的IDE真难用
* 微信的API需要逐个学习理解：[小程序API](https://mp.weixin.qq.com/debug/wxadoc/dev/api/)
* JavaScript 需要从基础开始学起
* 调试工具学习

在**Quick Start** 模板代码的基础上，实现了登录后显示 "Hello 唐尤华"

## app.js
这里是微信小程序的主程序，理解为 **main()** 吧

``` 
App({
})
```

这里做了几件事：
* **onLaunch**：监听小程序初始化，只调用一次
* 定义了 `globalData`：各个页面调用的全局变量，`app.globalData`

**初始化 onLaunch**
这里通过小程序API实现了获取 logs 本地缓存，登录，获取用户信息
* wx.getStorageSync / wx.setStorageSync：获取设置本地缓存
* wx.login：**注意，在没有设置小程序AppID的情况下，这里是模拟返回**
* wx.getSetting ：获取用户信息

所有的API详细说明可以在 [这里](https://mp.weixin.qq.com/debug/wxadoc/dev/api/) 查到

## 修改代码，让登录信息显示为"Hello 用户名"
在 `index.xml` 中，有显示 Hello World 的地方

```
<text class="user-motto">{{motto}}}</text>
改为
<text class="user-motto">Hello {{userInfo.nickName}}</text>
```

修改完成重新编译，点击登录，就可以看到结果啦

## 用到的调试工具
1 在调试工具下选择 Storage 可以看到记录登录日期的数组，保存了登录的时间
2 重新**编译**，登录，会增加一条当前登录时间
3 点**清缓存**，会把本地的缓存清掉，可以看到数组没有了

## 待学习的内容
* JavaScript基础
* 熟读[小程序API](https://mp.weixin.qq.com/debug/wxadoc/dev/api/)、[框架API](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/MINA.html)
