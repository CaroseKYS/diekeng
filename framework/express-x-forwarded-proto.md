# express 对 X-Forwarded-Proto 头部的支持前提是设置 "trust proxy"

## 现象描述
当负载均衡(nginx)设置了 `X-Forwarded-Proto` 头部为 `https` 时，如果 `express` 不设置 `trust proxy`，那么 `req.protocol` 属性永远是 `http`。`sinopia` 就有这个bug。

## 原因分析
没有激活 `trust proxy` 设置。

## 解决方案
`app.set('trust proxy', true);`
具体设置方法请参考[这里](https://expressjs.com/zh-cn/guide/behind-proxies.html)。