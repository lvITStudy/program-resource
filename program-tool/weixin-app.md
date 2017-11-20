# 微信小程序

* [开发文档](#wxdoc)
    * [小程序API](#wxapi)
    * [MINA框架](#mina)
    * [WeUI组件](#weui)
* 教程
    * [官网简易教程](https://mp.weixin.qq.com/debug/wxadoc/dev/)
* 学习日志
    * [X天小程序开发速度入门--第1天](../program-blog/learn-weixin-app-day1.md)
    * [X天小程序开发速度入门--第2天](../program-blog/learn-weixin-app-day2.md)
    * [X天小程序开发速度入门--第3天](../program-blog/learn-weixin-app-day3.md)
    * [X天小程序开发速度入门--第4天](../program-blog/learn-weixin-app-day4.md)
    * [X天小程序开发速度入门--第5天](../program-blog/learn-weixin-app-day5.md)
    * [X天小程序开发速度入门--第6天](../program-blog/learn-weixin-app-day6.md)
* 练习项目
* 相关技术
    * 前端
        * JavaScript
    * 后台
    * HTTP
    * 设计
    * 产品
    * 维护
* 其他资源
    * [官网](https://mp.weixin.qq.com/)
    * [微信开发者工具 ](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/download.html?t=1510576089)
        * [基础库](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/client-lib.html)
    * [微信开发者社区](https://developers.weixin.qq.com/home?token=137700584&lang=zh_CN)
    * 注意事项
        * [要求真机调试的功能](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/notsupport.html)
        * [不支持的ES6 API](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/details.html#客户端es6-api-支持情况)

<h2 id="wxdoc">开发文档</h2>

<h3>微信开发者文档</h3>

[文档主页](https://mp.weixin.qq.com/debug/wxadoc/dev/index.html)

* [微信开发者工具简介](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/devtools.html)

<h3 id="wxapi">小程序API</h3>

[API文档](https://mp.weixin.qq.com/debug/wxadoc/dev/api/)

* [网络](#wxapi-net)
* 媒体
    * [图片](#wxapi-img)
    * [录音及管理](#wxapi-record)
    * [音乐播放](#wxapi-audio)
    * [视频播放](#wxapi-video)
* [文件](#wxapi-file)
* [数据缓存](#wxapi-storage)
* [位置](#wxapi-location)
* [设备](#wxapi-device)
    * 系统信息
    * 网络状态
    * 加速度计
    * 罗盘
    * 拨打电话
    * 扫码
    * 剪切板
    * 蓝牙
    * iBeacon
    * 屏幕亮度
    * 用户截屏事件
    * 震动
    * 手机联系人
* [界面交互](#wxapi-react)
    * 交互反馈
    * 设置导航条
    * 设置置顶信息
    * 导航
    * 动画
    * 位置
    * 绘图
    * 下拉刷新
* [WXML节点信息](#wxapi-)
* [第三方平台](#wxapi-)
* [开放接口](#wxapi-)
* [数据](#wxapi-)
* [拓展接口](#wxapi-)
* [调试接口](#wxapi-)

<h4 id="wxapi-net">网络</h4>

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.request | 发起网络请求 | | |
| wx.uploadFile | 上传文件 | | |
| wx.downloadFile | 下载文件 | | |
| wx.connectSocket | 创建 WebSocket 连接 | | |
| wx.onSocketOpen | 监听 WebSocket 打开 | | |
| wx.onSocketError | 监听 WebSocket 错误 | | |
| wx.sendSocketMessage | 发送 WebSocket 消息 | | |
| wx.onSocketMessage | 接受 WebSocket 消息 | | |
| wx.closeSocket | 关闭 WebSocket 连接 | | |
| wx.onSocketClose | 监听 WebSocket 关闭 | | |

<h4 id="wxapi-img">图片</h4>

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.chooseImage | 从本地相册选择图片或使用相机拍照 | | |
| wx.previewImage | 预览图片 | | |
| wx.getImageInfo | 获取图片信息 | | |
| wx.saveImageToPhotosAlbum | 保存图片到系统相册 | | |

<h4 id="wxapi-record">录音及管理</h4>

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.startRecord | 开始录音 | 1.6.0 版本开始，本接口不再维护。建议使用能力更强的 wx.getRecorderManager 接口 | |
| wx.stopRecord | 停止录音 | | |
| wx.getRecorderManager | 获取全局唯一的录音管理器 `recorderManager` | 基础库 1.6.0 开始支持 | |

<h4 id="wxapi-audio">音乐播放</h4>

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.playVoice | 开始播放语音 | 同时只允许一个语音文件正在播放，如果前一个语音文件还没播放完，将中断前一个语音播放 | 1.6.0 版本开始，本接口不再维护。建议使用能力更强的 [wx.createInnerAudioContext](https://mp.weixin.qq.com/debug/wxadoc/dev/api/createInnerAudioContext.html) 接口 |
| wx.pauseVoice | 暂停正在播放的语音 | 再次调用wx.playVoice播放同一个文件时，会从暂停处开始播放。如果想从头开始播放，需要先调用 wx.stopVoice | |
| wx.stopVoice | 结束播放语音 |  | |
| wx.getBackgroundAudioPlayerState | 获取后台音乐播放状态 | 1.2.0 版本开始，本接口不再维护。建议使用能力更强的 [wx.getBackgroundAudioManager](https://mp.weixin.qq.com/debug/wxadoc/dev/api/getBackgroundAudioManager.html) 接口 | |
| wx.playBackgroundAudio | 使用后台播放器播放音乐 | 微信客户端来说，只能同时有一个后台音乐在播放。当用户离开小程序后，音乐将暂停播放；当用户点击“显示在聊天顶部”时，音乐不会暂停播放；当用户在其他小程序占用了音乐播放器，原有小程序内的音乐将停止播放 | |
| wx.pauseBackgroundAudio | 暂停播放音乐 | | |
| wx.seekBackgroundAudio | 控制音乐播放进度 | | |
| wx.stopBackgroundAudio | 停止播放音乐 | | |
| wx.onBackgroundAudioPlay | 监听音乐播放 | | |
| wx.onBackgroundAudioPause |监听音乐暂停 | | |
| wx.onBackgroundAudioStop | 监听音乐停止 | | |
| wx.getBackgroundAudioManager | 获取全局唯一的背景音频管理器 `backgroundAudioManager` | 基础库 1.2.0 开始支持 | |
| wx.createAudioContext | 创建并返回 audio 上下文 `audioContext` 对象 | 1.6.0 版本开始，本接口不再维护。建议使用能力更强的 [wx.createInnerAudioContext](https://mp.weixin.qq.com/debug/wxadoc/dev/api/createInnerAudioContext.html) 接口 | |
| wx.createInnerAudioContext | 创建并返回内部 audio 上下文 `innerAudioContext` 对象 | 本接口是 wx.createAudioContext 升级版 | |

<h4 id="wxapi-video">视频播放</h4>

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.chooseVideo | 拍摄视频或从手机相册中选视频，返回视频的临时文件路径 | | |
| wx.saveVideoToPhotosAlbum | 保存视频到系统相册。需要用户授权 [scope.writePhotosAlbum](https://mp.weixin.qq.com/debug/wxadoc/dev/api/authorize-index.html) | | |
| wx.createVideoContext | 创建并返回 video 上下文 `videoContext` 对象 | | |
| wx.createCameraContext | 创建并返回 camera 上下文 `cameraContext` 对象，`cameraContext` 与页面的 `camera` 组件绑定 | 一个页面只能有一个camera，通过它可以操作对应的 `<camera/>` 组件 | |

<h4  id="wxapi-file">文件</h4>

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.saveFile | 保存文件到本地 | | |
| wx.getFileInfo | 获取文件信息 | | |
| wx.getSavedFileList | 获取本地已保存的文件列表 | | |
| wx.getSavedFileInfo | 获取本地文件的文件信息 | 只能用于获取已保存到本地的文件，若需要获取临时文件信息，请使用 wx.getFileInfo 接口 | |
| wx.removeSavedFile | 删除本地存储的文件 | | |
| wx.openDocument | 新开页面打开文档 | 支持格式：doc, xls, ppt, pdf, docx, xlsx, pptx | |

<h4 id="wxapi-storage">数据缓存</h4>

本地数据存储的大小**限制为 10MB**

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.setStorage | 将数据存储在本地缓存中指定的 key 中 | 会覆盖掉原来该 key 对应的内容，这是一个异步接口 | |
| wx.setStorageSync | 将 data 存储在本地缓存中指定的 key 中 | 会覆盖掉原来该 key 对应的内容，这是一个同步接口 | |
| wx.getStorage | 从本地缓存中异步获取指定 key 对应的内容 |  | |
| wx.getStorageSync | 从本地缓存中同步获取指定 key 对应的内容 |  | |
| wx.getStorageInfo | 异步获取当前storage的相关信息 |  | |
| wx.getStorageInfoSync | 同步获取当前storage的相关信息 |  | |
| wx.removeStorage | 从本地缓存中异步移除指定 key |  | |
| wx.removeStorageSync | 从本地缓存中同步移除指定 key |  | |
| wx.clearStorage | 清理本地数据缓存 |  | |
| wx.clearStorageSync() | 同步清理本地数据缓存 |  | |


<h4 id="wxapi-location">位置</h4>

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.getLocation | 获取当前的地理位置、速度 | 用户离开小程序后，此接口无法调用；当用户点击“显示在聊天顶部”时，此接口可继续调用 | |
| wx.chooseLocation | 打开地图选择位置 | 需要[用户授权](https://mp.weixin.qq.com/debug/wxadoc/dev/api/authorize-index.html) scope.userLocation | |
| wx.openLocation | ​使用微信内置地图查看位置 | 需要[用户授权](https://mp.weixin.qq.com/debug/wxadoc/dev/api/authorize-index.html) scope.userLocation | |
| wx.createMapContext | 创建并返回 map 上下文 `mapContext` 对象 | | |

<h4 id="wxapi-device">设备</h4>

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.getSystemInfo | 获取系统信息 | | |
| wx.getSystemInfoSync | 获取系统信息同步接口 | | |
| wx.canIUse | 判断小程序的API，回调，参数，组件等是否在当前版本可用 | | |
| wx.getNetworkType | 获取网络类型 | | |
| wx.onNetworkStatusChange | 监听网络状态变化 | | |
| wx.onAccelerometerChange | 监听加速度数据 | 频率：5次/秒，接口调用后会自动开始监听，可使用 `wx.stopAccelerometer` 停止监听 | |
| wx.startAccelerometer | 开始监听加速度数据 | | |
| wx.stopAccelerometer | 停止监听加速度数据 | | |
| wx.onCompassChange | 监听罗盘数据 | 频率：5次/秒，接口调用后会自动开始监听，可使用 `wx.stopCompass` 停止监听 | |
| wx.startCompass | 开始监听罗盘数据 | | |
| wx.stopCompass | 停止监听罗盘数据 | | |
| wx.makePhoneCall | 拨打电话 | |
| wx.scanCode | 调起客户端扫码界面，扫码成功后返回对应的结果 | |
| wx.setClipboardData | 设置系统剪贴板的内容 | | |
| wx.getClipboardData | 获取系统剪贴板内容 | | |
| wx.onUserCaptureScreen | 监听用户主动截屏事件 | 用户使用系统截屏按键截屏时触发此事件 | |
| wx.setScreenBrightness | 设置屏幕亮度 | | |
| wx.getScreenBrightness | 获取屏幕亮度 | | |
| wx.setKeepScreenOn | 设置是否保持常亮状态 | 仅在当前小程序生效，离开小程序后设置失效 | |
| wx.vibrateLong | 使手机发生较长时间的振动（400ms） | | |
| wx.vibrateShort | 使手机发生较短时间的振动（15ms） | | |
| wx.addPhoneContact | 调用后，用户可以选择将该表单以“新增联系人”或“添加到已有联系人”的方式，写入手机系统通讯录，完成手机通讯录联系人和联系方式的增加。 | | |

<h5>蓝牙</h5>

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.openBluetoothAdapter | 初始化小程序蓝牙模块 | 生效周期为调用 `wx.openBluetoothAdapter` 至调用 `wx.closeBluetoothAdapter` 或小程序被销毁为止 | |
| wx.closeBluetoothAdapter | 关闭蓝牙模块，使其进入未初始化状态 | 调用该方法将断开所有已建立的链接并释放系统资源。建议在使用小程序蓝牙流程后调用，与 `wx.openBluetoothAdapter` 成对调用 | |
| wx.getBluetoothAdapterState | 获取本机蓝牙适配器状态 | | |
| wx.onBluetoothAdapterStateChange | 监听蓝牙适配器状态变化事件 | | |
| wx.startBluetoothDevicesDiscovery | 开始搜寻附近的蓝牙外围设备 | 该操作比较耗费系统资源，请在搜索并连接到设备后调用 stop 方法停止搜索 | |
| wx.stopBluetoothDevicesDiscovery | 停止搜寻附近的蓝牙外围设备 | | |
| wx.getBluetoothDevices | 获取在小程序蓝牙模块生效期间所有已发现的蓝牙设备 | 包括已经和本机处于连接状态的设备 | |
| wx.getConnectedBluetoothDevices | 根据 uuid 获取处于已连接状态的设备 | | |
| wx.onBluetoothDeviceFound | 监听寻找到新设备的事件 | | |
| wx.createBLEConnection | 连接低功耗蓝牙设备 | | |
| wx.closeBLEConnection | 断开与低功耗蓝牙设备的连接 | | |
| wx.getBLEDeviceServices | 监听低功耗蓝牙连接的错误事件 | 包括设备丢失，连接异常断开等等 | |
| wx.getBLEDeviceCharacteristics | 获取蓝牙设备所有 service（服务） | | |
| wx.readBLECharacteristicValue | 读取低功耗蓝牙设备的特征值的二进制数据值 | 必须设备的特征值支持 `read` 才可以成功调用，具体参照 characteristic 的 properties 属性 | |
| wx.writeBLECharacteristicValue | 向低功耗蓝牙设备特征值中写入二进制数据 | 必须设备的特征值支持 `write` 才可以成功调用，具体参照 characteristic 的 properties 属性 | |
| wx.notifyBLECharacteristicValueChange | 启用低功耗蓝牙设备特征值变化时的 notify 功能，订阅特征值 | 必须设备的特征值支持 `notify` 或者 `indicate` 才可以成功调用 | |
| wx.onBLEConnectionStateChange | 监听低功耗蓝牙设备的特征值变化 | 必须先启用 `notify` 接口才能接收到设备推送的 notification | |
| wx.onBLECharacteristicValueChange |  | | |

**蓝牙错误码列表**

|错误码 |说明 |备注 |
| :------------ |:---------------| :-----|
| 0 | ok  | 正常 |
| 10000 | not init    | 未初始化蓝牙适配器 |
| 10001 | not available   | 当前蓝牙适配器不可用 |
| 10002 | no device   | 没有找到指定设备 |
| 10003 | connection fail | 连接失败 |
| 10004 | no service  | 没有找到指定服务 |
| 10005 | no characteristic   | 没有找到指定特征值 |
| 10006 | no connection   | 当前连接已断开 |
| 10007 | property not support    | 当前特征值不支持此操作 |
| 10008 | system error    | 其余所有系统上报的异常 |
| 10009 | system not support |  Android 系统特有，系统版本低于 4.3 不支持BLE |

<h5>iBeacon</h5>

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.startBeaconDiscovery | 开始搜索附近的iBeacon设备 |  |  |
| wx.stopBeaconDiscovery | 停止搜索附近的iBeacon设备 |  |  |
| wx.getBeacons | 获取所有已搜索到的iBeacon设备 |  |  |
| wx.onBeaconUpdate | 监听 iBeacon 设备的更新事件 |  |  |
| wx.onBeaconServiceChange | 监听 iBeacon 服务的状态变化 |  |  |

**iBeacon错误码列表**

|错误码 |说明 |备注 |
| :------------ |:---------------| :-----|
| 0 |  ok | 正常 |
| 11000 |  unsupport  | 系统或设备不支持 |
| 11001 |  bluetooth service unavailable  | 蓝牙服务不可用 |
| 11002 |  location service unavailable   | 位置服务不可用 |
| 11003 |  already start  | 已经开始搜索 |

<h4 id="wxapi-react">界面交互</h4>

|API |功能 |说明 |示例 | 
| :------------ |:---------------| :-----| :-----|
| wx.showToast | 显示消息提示框 |  |  |
| wx.showLoading | 显示 loading 提示框 | 需主动调用 [wx.hideLoading](https://mp.weixin.qq.com/debug/wxadoc/dev/api/api-react.html#wxhideloading) 才能关闭提示框 |  |
| wx.hideToast | 隐藏消息提示框 |  |  |
| wx.hideLoading | 隐藏 loading 提示框 |  |  |
| wx.showModal | ​显示模态弹窗 |  |  |
| wx.showActionSheet | ​显示操作菜单 |  |  |
| wx.setNavigationBarTitle | 动态设置当前页面的标题 |  |  |
| wx.showNavigationBarLoading | 在当前页面显示导航条加载动画 |  |  |
| wx.hideNavigationBarLoading | 隐藏导航条加载动画 |  |  |
| wx.setNavigationBarColor |  |  |  |
| wx.setTopBarText | 动态设置置顶栏文字内容 |  |  |
| wx.navigateTo | 保留当前页面，跳转到应用内的某个页面 | 使用 `wx.navigateBack` 可以返回到原页面 |  |
| wx.redirectTo | 关闭当前页面，跳转到应用内的某个页面 |  |  |
| wx.switchTab | 跳转到 tabBar 页面，并关闭其他所有非 tabBar 页面 |  |  |
| wx.navigateBack | 关闭当前页面，返回上一页面或多级页面 | 可通过 `getCurrentPages()` 获取当前的页面栈，决定需要返回几层 |  |
| wx.reLaunch | 关闭所有页面，打开到应用内的某个页面 |  |  |
| wx.createAnimation | 创建一个动画实例[animation](https://mp.weixin.qq.com/debug/wxadoc/dev/api/api-animation.html#animation) | 调用实例的方法来描述动画。最后通过动画实例的`export`方法导出动画数据传递给组件的`animation`属性 |  |
| wx.pageScrollTo | 将页面滚动到目标位置 |  |  |
| wx.createSelectorQuery | 返回一个SelectorQuery对象实例 | 可以在这个实例上使用`select`等方法选择节点，并使用`boundingClientRect`等方法选择需要查询的信息 |  |
| Page.onPullDownRefresh | 在 Page 中定义 onPullDownRefresh 处理函数，监听该页面用户下拉刷新事件 | * 需要在 config 的window选项中开启 enablePullDownRefresh。
* 当处理完数据刷新后，wx.stopPullDownRefresh可以停止当前页面的下拉刷新 |  |
| wx.startPullDownRefresh | 开始下拉刷新，调用后触发下拉刷新动画，效果与用户手动下拉刷新一致 |  |  |
| wx.stopPullDownRefresh | 停止当前页面下拉刷新 |  |  |
| 绘图 |  |  |  |


* WXML节点信息
* 第三方平台
* 开放接口
* 数据
* 拓展接口
* 调试接口

<h3 id="mina">小程序框架 MINA</h3>

[MINA主页](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/MINA.html)

* [app.json配置](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/config.html)
* [WXML标签语言](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/)
* [WXSS样式表](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxss.html) 
*  [事件](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/event.html)

<h3 id="weui">小程序UI组件-WeUI</h3>

[基础组件](https://mp.weixin.qq.com/debug/wxadoc/dev/component/)

<h2>微信开发者工具</h2>

<h3>调试</h3>

* 调试器 Console：输入和调试代码，比起在debug里面查看变量方便很多
* 调试器 Wxml：可以直接查看wxml 转化后的界面，与chrome里面查看html的DOM模型一样
* 调试器 Source：查看源码，下断点，调试
* 调试器 AppData：查看数据非常方便，比如定义的userInfo、motto等信息
* 调试器 Storage：查看本地存储，配合清缓存调试
* 调试器 Network：查看网络调用，与后台通信时用到
* 调试器 Sensor：模拟地理位置和重力感应，高级功能（不大常用:P）

<h2>相关技术</h2>

<h3>JavaScript在小程序开发中的用法</h3>

<h4>箭头函数</h4>

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

<h4>逻辑运算符 &#124;&#124;</h4>

```
var logs = wx.getStorageSync('logs') || []
```

1 在调试，Source面板下断点
2 在调试，Console面板下输入 `wx.getStorageSync('logs')`
    * 初次运行或者清除缓存后，会返回空数组
3 上面这句，在 `wx.getStorageSync('logs')` 返回 `undefined` 情况下，会返回一个空数组
    * `undefined`  在条件语句中判定为 `false`

**上面语句的含义**：返回 logs 非空数组（本地缓存），或者返回空数组

<h4>数组操作 unshift</h4>

```
  onLaunch: function () {
    // 展示本地存储能力
    var logs = wx.getStorageSync('logs') || []
    logs.unshift(Date.now())
    wx.setStorageSync('logs', logs)
```

* `unshift()`  方法可向数组的开头添加一个或更多元素，并返回新的长度
* 小程序初始化完成  `onLaunch` 事件发生，会记录当前日期到 logs 数组，存储到本地缓存

<h4>this对象</h4>

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

<h4>全局变量</h4>

```
  globalData: {
    userInfo: null
  }
```
app.js 里定义了 `globalData` 全局变量，于是在各个地方都用到了，进行用户信息传递

理论上有两种方法可以查看  `globalData`  被调用的情况
* 右键菜单，查找所有引用：恩，没有用
*  `CTRL+SHIFT+F` 查找  `globalData`：可以看到，在 app.js 和 index.js 中分别进行了赋值和使用

<h4>console.log</h4>

```
  getUserInfo: function(e) {
    console.log(e)
```

这是很重要的调试技巧，上面的代码把 `UserInfo` 在Console面板中打印了出来

* Source面板下断点
* 执行 `console.log(e)` 或者 直接在Console面板下输入 `console.log(e)` 回车，都可以看到返回的用户信息 


