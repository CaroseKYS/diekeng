#iphone6 plus safari，子页面的宽度不受父页面中iframe大小的限制，当子页面的宽高大于父页面中iframe的宽高时，子页面的内容将全部可见

## 需要的效果图
![需要的效果图](./images/iframe1-1.jpg "需要的效果图")

上图中的小窗口是在一个 `iframe` 元素中 **嵌入** 了 **子页面**, 代码大致如下：
     
     <div style="width: 80%; height: 300px; margin: 0 auto;">
       <iframe src="./inner.html" style="width: 100%; height: 100%;"></iframe>
     </div>

## 存在bug的效果图
![需要的效果图](./images/iframe1-2.jpg "需要的效果图")

上图为在 `iphone` 自带的 `safari` 浏览器中打开页面时的效果图，当 `iframe` 中内嵌的页面未加载之前， `iframe` 的宽和高是正常的，当子页面加载完成之后，宽度就会发生变化，高度也相应改变。父页面中显示出来的 `iframe` 宽和高其实是子页面的真实宽高！也就是说子页面的宽高没有受到父页面中 `iframe` 高宽的限制。似乎该平台上的所有浏览器都有这样的问题。

## 解决方案

1. 为 `iframe` 元素加上 `scrolling="no"` 的属性.
2. 使用最高权限为 `iframe` 设置高宽： `width: XXpx!important`, 这样才能保证子页面的高宽不会将 `iframe` 撑开。也可以使用 `min-width` 或 `max-width` 等属性。

&nbsp;

    <iframe src="./inner.html" scrolling="no" style="width: 400px!important; height: 400px!important"></iframe>