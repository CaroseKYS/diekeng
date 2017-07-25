# 在 IE9 及以下版本的浏览器中，使用frame嵌套子页面的方式访问站点时，站点的cookie不会被发送到服务器端，服务器端设置的cookie无效

## 原因分析：
产生问题的根本原因是 IE 支持 [P3P](https://baike.baidu.com/item/p3p/426876?fr=aladdin) 策略，请参考。

## 解决方法：
在服务器端添加响应头部信息：`response.setHeader("P3P", "CP=CAO PSA OUR");`。
