---
title: 移动端常用meta标签收集
date: 2018-07-18 23:45:34
tags: [html, h5, meta]
---

```html
<!--图标引入-->
<link rel="short icon" style="image/x-icon" href="taobaoLogo.ico" />
<link rel="icon" style="image/x-icon" href="taobaoLogo.ico" />

<!--禁止用户手动的去改变页面的大小-->
<meta
  name="viewport"
  content="width=device-width,initial-scale=1,user-scalable=no"
/>

<!--开启对web app的支持-->
<meta name="apple-mobile-web-app-capable" content="yes" />

<!--主要是正对苹果手机将数字自动识别为号码-->
<meta name="format-detection" content="telephone=no" />

<!-- 忽略识别邮箱，主要是针对安卓手机会自动将符合邮箱格式的字符串识别为邮箱地址-->
<meta content="email=no" name="format-detection" />
<meta
  name="apple-itunes-app"
  content="app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL"
/>

<!-- 添加智能 App 广告条 Smart App Banner：告诉浏览器这个网站对应的app，并在页面上显示下载banner:https://developer.apple.com/library/ios/documentation/AppleApplications/Reference/SafariWebContent/PromotingAppswithAppBanners/PromotingAppswithAppBanners.html -->
<!-- 针对手持设备优化，主要是针对一些老的不识别viewport的浏览器，比如黑莓 -->
<meta name="HandheldFriendly" content="true" />

<!-- 微软的老式浏览器 -->
<meta name="MobileOptimized" content="320" />

<!-- uc强制竖屏 -->
<meta name="screen-orientation" content="portrait" />

<!-- QQ强制竖屏 -->
<meta name="x5-orientation" content="portrait" />

<!-- UC强制全屏 -->
<meta name="full-screen" content="yes" />

<!-- QQ强制全屏 -->
<meta name="x5-fullscreen" content="true" />

<!-- UC应用模式 -->
<meta name="browsermode" content="application" />

<!-- QQ应用模式 -->
<meta name="x5-page-mode" content="app" />

<!-- windows phone 点击无高光 -->
<meta name="msapplication-tap-highlight" content="no" />

<!-- 获取滚动条的滚动值 -->
window.scrollY window.scrollX

<!-- 禁止用户选择文本 -->
-webkit-user-select:none

<!-- 手机图片和视频上传 -->
<!-- 选择照片 -->
<input type="file" accept="image/*" />
<!-- 选择视频 -->
<input type="file" accept="video/*" />

<!-- 动画特效开启加速 -->
.div { -webkit-transform: translate3d(0, 0, 0); -moz-transform: translate3d(0,
0, 0); -ms-transform: translate3d(0, 0, 0); transform: translate3d(0, 0, 0); /*
Other transform properties here */ }

<!-- 设置placeholder时候 focus时候文字没有隐藏 -->
input:focus::-webkit-input-placeholder{ opacity: 0; }
```
