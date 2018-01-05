# Weixin To Alipay Coupon

- 微信中直接一键领取支付宝红包
- One click to obtain the alipay coupon from Weixin
- 微信中可直接访问 =>  http://sougg.com/wy
- [一键领取](http://sougg.com/wy)

# 参考代码如下

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link rel="icon" href="https://i.alipayobjects.com/common/favicon/favicon.ico" type="image/x-icon">
    <link rel="shortcut icon" href="https://i.alipayobjects.com/common/favicon/favicon.ico" type="image/x-icon">
    <title>正在打开支付宝，请稍候……</title>
</head>
<body>
<script type="text/javascript">
  var url1 = "https://qr.alipay.com/c1x00262bq9men4erwuwe2a";
  var url2 = "https://qr.alipay.com/c1x00262bq9men4erwuwe2a";
  function is_weixin() {
      if (/MicroMessenger/i.test(navigator.userAgent)) {
          return true
      } else {
          return false
      }
  }

  function is_android() {
      var ua = navigator.userAgent.toLowerCase();
      if (ua.match(/(Android|SymbianOS)/i)) {
          return true
      } else {
          return false
      }
  }

  function is_ios() {
      var ua = navigator.userAgent.toLowerCase();
      if (/iphone|ipad|ipod/.test(ua)) {
          return true
      } else {
          return false
      }
  }

  function android_auto_jump() {
      WeixinJSBridge.invoke("jumpToInstallUrl", {}, function (e) {});
      window.close();
      WeixinJSBridge.call("closeWindow")
  }

  function ios_auto_jump() {
      if (url1 != "") {
          location.href = url1
      } else {
          window.close();
          WeixinJSBridge.call("closeWindow")
      }
  }

  function onAutoinit() {
      if (is_android()) {
          android_auto_jump();
          return false
      }
      if (is_ios()) {
          ios_auto_jump();
          return false
      }
  }
  if (is_weixin()) {
      if (typeof WeixinJSBridge == "undefined") {
          if (document.addEventListener) {
              document.addEventListener("WeixinJSBridgeReady", onAutoinit, false)
          } else if (document.attachEvent) {
              document.attachEvent("WeixinJSBridgeReady", onAutoinit);
              document.attachEvent("onWeixinJSBridgeReady", onAutoinit)
          }
      } else {
          onAutoinit()
      }
  } else {
      if (url2 != "") {
          location.href = url2
      } else {
          window.close()
      }
  }
</script>
</body>
</html>
```
