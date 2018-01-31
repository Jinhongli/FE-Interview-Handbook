## 描述一下 CSS 选择器的优先级

浏览器在计算一个元素的 CSS 规则时，当多个选择器出现冲突时，就会根据 CSS 选择器的优先级来决定。CSS 选择器的优先级从高到低，分别是：

1. ID 选择器（`#example`）
2. 类选择器（`.example`），属性选择器（`[type="text"]`），伪类选择器（`:hover`）
3. 元素选择器（`div`），伪元素选择器（`::before`）

计算 CSS 规则的方法：

* 把上面的优先级量化为十进制的数，从高到底分别是：100, 10, 1。然后在 CSS 规则中找到所有的选择器，然后将它们的优先级求和就是最终的结果。
* 通用选择器（`*`），连接符（`+`, `>`, `~`, ``），否定伪类（`:not()`）对优先级没有影响（优先级最低），计算时可以忽略。
* 带有`!important`属性的优先级最高。
* 同优先级下，选择位置靠后的属性。

比如：

* `div#root`的优先级：100 + 1 = 101
* `p.red`的优先级：10 + 1 = 11
* `div p`的优先级：1 + 1 = 2

**参考**

1. [https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity)

## CSS 里面的`id`和`class`有什么区别？

* `id`：唯一的元素标识，可以作为页面 url 的 hash 以便于跳转时直接展示该元素。一个元素只允许有一个`id`属性。
* `class`：可以多个元素共用，一般用于获取元素并设置样式。

## 重置（reset）和统一（normalize）CSS 有什么区别，你会选择哪种？

* reset：把所有元素的基础样式全部重置，包括`margin`，`padding`，`font-size`等等都设置为一样的，所以需要重新定义常见元素样式。
* normalize：把所有元素的基础样式都设置为统一值，来顶替浏览器的默认值。

对于一个非定制的网站，应该选择 reset 的方式，因为其可能会有很多特定样式的元素，需要对这些元素完全重写其样式，所以应该重置所有样式。但是对于那些比较简单，或者说不需要太多自定义元素样式的网页来说，normalize 的方式更为合适。只要保证元素的基础样式在所有浏览器一直就可以了。

对于我个人而言，我更倾向于针对网站写一个定制化的 normalize，来获得一个默认样式，之后再重写定制元素的样式。

**参考**

1. [https://stackoverflow.com/questions/6887336/what-is-the-difference-between-normalize-css-and-reset-css](https://stackoverflow.com/questions/6887336/what-is-the-difference-between-normalize-css-and-reset-css)

## 描述一下`float`

`float`在 CSS 用于布局，设为`float`的元素会向左或右移动，直到其边缘碰到容器边缘或其他浮动元素。

* 浮动元素会影响其周围元素的位置，且自身会脱离文档的普通流，但是并不会完全脱离文档流（仍然在文档流中占有位置）。
* 浮动元素的周围元素内的文字，不会被浮动元素遮盖，而是环绕其周围。

说到浮动就不的不提到清除浮动，最常见的问题就是如果父元素的所有子元素都是浮动的，那么其高度就会折叠变为 0。

清除浮动的方法主要有：

* 设置`clear`属性。
* 兼容所有浏览器的`clearfix`，把`clear`属性写在`::after`伪元素，避免直接改写内容元素。
* 触发 BFC 的方式来清除浮动。比如`overflow: auto`，或者`overflow: hidden`

**参考**

1. [http://www.w3school.com.cn/css/css_positioning_floating.asp](http://www.w3school.com.cn/css/css_positioning_floating.asp)

## `z-index`和层叠上下文

当元素出现重叠时，`z-index`属性用于决定谁会覆盖其他元素（通常来说`z-index`较大的元素会覆盖较小的一个）。对于一个已经定位的元素，设置`z-index`会：

1. 指定元素当前层叠上下文的层级
2. 决定是否创建新的本地层叠上下文

如果不指定`z-index`，那么就按照 DOM 结构的顺序（下面的元素会遮盖上面），但已定位的元素会始终在普通元素上方。

层叠上下文是一种三维概念，指元素在面向用户的方向上（Z 轴）会根据自身属性按照优先级会分为很多层，然后进行堆叠。

在层叠上下文中，子元素的`z-index`值相对于本地上下文，并且与外部的其他元素独立。举个例子：元素 A 上面有一个兄弟元素 B，A 有一个子元素 C，那么即使 C 设置的`z-index`更高，也不会覆盖 B 元素。

层叠上下文堆叠的顺序是先内再外，即当元素的内容层叠完毕之后，再按照元素的层级插入到父级的层叠上下文中。

文档中的层叠上下文由满足下列条件的元素形成（常见的）：

* 根元素（HTML）
* `z-index`不为`auto`的绝对定位、相对定位、flex-item 元素
* `position: fixed`的元素
* `opacity`小于 1 的元素
* `transform`、`filter`、`perspective`不为`none`的元素

**参考**

1. [https://developer.mozilla.org/zh-CN/docs/Web/CSS/z-index](https://developer.mozilla.org/zh-CN/docs/Web/CSS/z-index)
1. [https://css-tricks.com/almanac/properties/z/z-index/](https://css-tricks.com/almanac/properties/z/z-index/)
1. [https://philipwalton.com/articles/what-no-one-told-you-about-z-index/](https://philipwalton.com/articles/what-no-one-told-you-about-z-index/)
1. [https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)

## 描述下 BFC 是什么

BFC（块格式化上下文），是一个 CSS 布局用的区域（上下文）。可以理解将触发了 BFC 的元素（或者就叫 BFC 元素）比作一个盒子，这个盒子具有以下特性（相比于没有触发 BFC 的元素）：

1. 盒子内元素布局与盒子外元素相互独立（与层叠上下文中计算`z-index`优先级类似）。
2. 计算盒子高度时，考虑其所有子元素，浮动元素也会参与计算。
3. 浮动元素与 BFC 元素不会层叠。

BFC 能够解决哪些问题：

1. **外边距折叠：**相邻元素的外边距会发生折叠，取两者中较大值。利用特性 1，使其中一个元素触发 BFC，那么两个元素的布局就会独立，避免外边距重叠。
2. **清除浮动，计算元素高度：**当一个元素内所有的子元素均是浮动元素时，其高度为 0。利用特性 2，使父元素触发 BFC，会在计算高度时包含浮动元素。
3. **布局：**常见的两栏布局（固定宽度的侧栏 + 剩余宽度的主栏），侧栏使用浮动之后，就会与主栏发生层叠。利用特性 3，使主栏触发 BFC，占据容器剩余宽度。

什么条件下会触发 BFC：

* 根元素`<html>`
* `float`不为`none`的元素
* `overflow`不为`visible`的元素
* `position`为`absolute`或`fixed`的元素
* `display`为`inline-block`，`table-cell`，`table-caption`，`flex`，`inline-flex`的元素'

**参考**

1. [https://segmentfault.com/a/1190000005116275](https://segmentfault.com/a/1190000005116275)
2. [http://www.html-js.com/article/1866](http://www.html-js.com/article/1866)

## 清除浮动都有哪些手段，分别适用于什么情况？

1. 添加空`div`元素：`<div style="clear: both;"></div>`
2. 使用`clearfix`：把`clear`属性写在隐藏的`::after`伪元素上
3. 利用 BFC：对父元素设置`overflow: auto`或者`overflow: hidden`

最好用`clearfix`的方式，因为另外两种都会带来一定的副作用：额外的元素；对内部布局产生影响。

## 解释下什么是 CSS 雪碧图，以及你会如何实现？

CSS 雪碧图是指将多个图片合并为一个图片的技术，通常用于 icon 图片。

1. 使用雪碧图制作工具或这 PhotoShop，将多个图片放在一个图片中。
2. 通过`background-image`，`background-position`来控制如何显示图片。

雪碧图的优点：

* 减小 HTTP 请求次数（HTTP2 不再有并发限制，所以不存在此问题）

**参考**

1. [https://css-tricks.com/css-sprites/](https://css-tricks.com/css-sprites/)
2. [https://docs.google.com/presentation/d/1r7QXGYOLCh4fcUq0jDdDwKJWNqWK1o4xMtYpKZCJYjM/present?slide=id.p19](https://docs.google.com/presentation/d/1r7QXGYOLCh4fcUq0jDdDwKJWNqWK1o4xMtYpKZCJYjM/present?slide=id.p19)

## 视觉上隐藏元素的方法都有哪些？

与无障碍（可访问性）功能有点关系（a11y）。

* `visibility: hidden`：元素虽然看不见，但依然会在文档流中并占据位置。
* `width: 0; height: 0;`：让元素在文档流中占据位置为 0，视觉上也就看不到。
* `position: absolute; left: -99999px`：让元素脱离文档流并移出屏幕外。
* `text-indent: -9999px`：将文字移出屏幕外。（仅作用于块级元素内的文字）
* 元数据：例如使用 Schema.org，RDF 以及 JSON-LD。
* WAI-ARIA：专门用于无障碍功能技术（Bootstrap 中`role`和`aria-*`属性）

**参考**

1. [http://www.zhangxinxu.com/wordpress/2012/03/wai-aria-%E6%97%A0%E9%9A%9C%E7%A2%8D%E9%98%85%E8%AF%BB/](http://www.zhangxinxu.com/wordpress/2012/03/wai-aria-%E6%97%A0%E9%9A%9C%E7%A2%8D%E9%98%85%E8%AF%BB/)
2. [http://a11yproject.com/](http://a11yproject.com/)

## 编写高效 CSS 需要注意哪些问题？

首先，浏览器匹配 CSS 选择器的顺序是从右到左（最右的选择器成为关键选择器）。浏览器首先根据关键选择器筛选 DOM 中的元素，然后再向上遍历其祖先元素检查选择器是否匹配。因此：

1. 避免最后的关键选择器是标签选择器或这通用选择器，以减少筛选结果的数量。
2. 使用更短的选择器规则，以加快匹配速度。

注意 CSS 属性是否会引起的重排（reflow）以及重汇（repaint）。尤其要尽可能的避免重排，因为其对性能损耗非常大（浏览器布局 Layout 需要花费的时间非常大）。

**参考**

1. [https://developers.google.com/web/fundamentals/performance/rendering/](https://developers.google.com/web/fundamentals/performance/rendering/)
2. [https://csstriggers.com/](https://csstriggers.com/)
