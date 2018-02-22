# CSS 相关问题

  - [描述一下 CSS 选择器的优先级](#%E6%8F%8F%E8%BF%B0%E4%B8%80%E4%B8%8B-css-%E9%80%89%E6%8B%A9%E5%99%A8%E7%9A%84%E4%BC%98%E5%85%88%E7%BA%A7)
  - [CSS 里面的`id`和`class`有什么区别？](#css-%E9%87%8C%E9%9D%A2%E7%9A%84id%E5%92%8Cclass%E6%9C%89%E4%BB%80%E4%B9%88%E5%8C%BA%E5%88%AB%EF%BC%9F)
  - [重置（reset）和统一（normalize）CSS 有什么区别，你会选择哪种？](#%E9%87%8D%E7%BD%AE%EF%BC%88reset%EF%BC%89%E5%92%8C%E7%BB%9F%E4%B8%80%EF%BC%88normalize%EF%BC%89css-%E6%9C%89%E4%BB%80%E4%B9%88%E5%8C%BA%E5%88%AB%EF%BC%8C%E4%BD%A0%E4%BC%9A%E9%80%89%E6%8B%A9%E5%93%AA%E7%A7%8D%EF%BC%9F)
  - [描述一下`float`](#%E6%8F%8F%E8%BF%B0%E4%B8%80%E4%B8%8Bfloat)
  - [`z-index`和层叠上下文](#z-index%E5%92%8C%E5%B1%82%E5%8F%A0%E4%B8%8A%E4%B8%8B%E6%96%87)
  - [描述下 BFC 是什么](#%E6%8F%8F%E8%BF%B0%E4%B8%8B-bfc-%E6%98%AF%E4%BB%80%E4%B9%88)
  - [清除浮动都有哪些手段，分别适用于什么情况？](#%E6%B8%85%E9%99%A4%E6%B5%AE%E5%8A%A8%E9%83%BD%E6%9C%89%E5%93%AA%E4%BA%9B%E6%89%8B%E6%AE%B5%EF%BC%8C%E5%88%86%E5%88%AB%E9%80%82%E7%94%A8%E4%BA%8E%E4%BB%80%E4%B9%88%E6%83%85%E5%86%B5%EF%BC%9F)
  - [解释下什么是 CSS 雪碧图，以及你会如何实现？](#%E8%A7%A3%E9%87%8A%E4%B8%8B%E4%BB%80%E4%B9%88%E6%98%AF-css-%E9%9B%AA%E7%A2%A7%E5%9B%BE%EF%BC%8C%E4%BB%A5%E5%8F%8A%E4%BD%A0%E4%BC%9A%E5%A6%82%E4%BD%95%E5%AE%9E%E7%8E%B0%EF%BC%9F)
  - [视觉上隐藏元素的方法都有哪些？](#%E8%A7%86%E8%A7%89%E4%B8%8A%E9%9A%90%E8%97%8F%E5%85%83%E7%B4%A0%E7%9A%84%E6%96%B9%E6%B3%95%E9%83%BD%E6%9C%89%E5%93%AA%E4%BA%9B%EF%BC%9F)
  - [编写高效 CSS 需要注意哪些问题？](#%E7%BC%96%E5%86%99%E9%AB%98%E6%95%88-css-%E9%9C%80%E8%A6%81%E6%B3%A8%E6%84%8F%E5%93%AA%E4%BA%9B%E9%97%AE%E9%A2%98%EF%BC%9F)
  - [使用 CSS 预处理器的优点](#%E4%BD%BF%E7%94%A8-css-%E9%A2%84%E5%A4%84%E7%90%86%E5%99%A8%E7%9A%84%E4%BC%98%E7%82%B9)
  - [如何在网页中使用非标准的字体](#%E5%A6%82%E4%BD%95%E5%9C%A8%E7%BD%91%E9%A1%B5%E4%B8%AD%E4%BD%BF%E7%94%A8%E9%9D%9E%E6%A0%87%E5%87%86%E7%9A%84%E5%AD%97%E4%BD%93)
  - [描述下浏览器如何将元素匹配到相应的选择器规则](#%E6%8F%8F%E8%BF%B0%E4%B8%8B%E6%B5%8F%E8%A7%88%E5%99%A8%E5%A6%82%E4%BD%95%E5%B0%86%E5%85%83%E7%B4%A0%E5%8C%B9%E9%85%8D%E5%88%B0%E7%9B%B8%E5%BA%94%E7%9A%84%E9%80%89%E6%8B%A9%E5%99%A8%E8%A7%84%E5%88%99)
  - [描述下盒模型](#%E6%8F%8F%E8%BF%B0%E4%B8%8B%E7%9B%92%E6%A8%A1%E5%9E%8B)
  - [`* { box-sizing: border-box; }`是干什么的？有什么好处？](#box-sizing-border-box-%E6%98%AF%E5%B9%B2%E4%BB%80%E4%B9%88%E7%9A%84%EF%BC%9F%E6%9C%89%E4%BB%80%E4%B9%88%E5%A5%BD%E5%A4%84%EF%BC%9F)
  - [描述下`block`，`inline`，`inline-block`的区别](#%E6%8F%8F%E8%BF%B0%E4%B8%8Bblock%EF%BC%8Cinline%EF%BC%8Cinline-block%E7%9A%84%E5%8C%BA%E5%88%AB)
  - [都有哪些定位的属性，分别有什么不同？](#%E9%83%BD%E6%9C%89%E5%93%AA%E4%BA%9B%E5%AE%9A%E4%BD%8D%E7%9A%84%E5%B1%9E%E6%80%A7%EF%BC%8C%E5%88%86%E5%88%AB%E6%9C%89%E4%BB%80%E4%B9%88%E4%B8%8D%E5%90%8C%EF%BC%9F)
  - [有接触过 CSS`flex`布局以及栅格布局么？](#%E6%9C%89%E6%8E%A5%E8%A7%A6%E8%BF%87-cssflex%E5%B8%83%E5%B1%80%E4%BB%A5%E5%8F%8A%E6%A0%85%E6%A0%BC%E5%B8%83%E5%B1%80%E4%B9%88%EF%BC%9F)
  - [响应式（responsive）和自适应（adaptive）有什么区别？](#%E5%93%8D%E5%BA%94%E5%BC%8F%EF%BC%88responsive%EF%BC%89%E5%92%8C%E8%87%AA%E9%80%82%E5%BA%94%EF%BC%88adaptive%EF%BC%89%E6%9C%89%E4%BB%80%E4%B9%88%E5%8C%BA%E5%88%AB%EF%BC%9F)
  - [相比于使用`absolute`定位，使用`translate()`有哪些好处？](#%E7%9B%B8%E6%AF%94%E4%BA%8E%E4%BD%BF%E7%94%A8absolute%E5%AE%9A%E4%BD%8D%EF%BC%8C%E4%BD%BF%E7%94%A8translate%E6%9C%89%E5%93%AA%E4%BA%9B%E5%A5%BD%E5%A4%84%EF%BC%9F)

## 描述一下 CSS 选择器的优先级

同一个元素有可能会被多个选择器选中，也就有可能出现同一个属性带被设置不同值（声明冲突）的情况。这个时候，CSS标准会规定哪个声明优先级最高并生效。CSS 选择器的优先级从高到低，分别是：

1. ID 选择器（`#example`）
2. 类选择器（`.example`），属性选择器（`[type="text"]`），伪类选择器（`:hover`）
3. 元素选择器（`div`），伪元素选择器（`::before`）

计算 CSS 规则的方法：

* 把选择器的优先级量化为十进制数，从高到底分别是：100, 10, 1。然后在 CSS 规则中找到所有的选择器，然后将它们的优先级求和。
* 通用选择器（`*`），连接符（`+`, `>`, `~`, ` `），否定伪类（`:not()`）对优先级没有影响（优先级最低），计算时可以忽略。
* 带有`!important`后缀的声明优先级最高。
* 同优先级下，选择位置靠后的属性。

比如：

* `div#root`的优先级：100 + 1 = 101
* `p.red`的优先级：10 + 1 = 11
* `div p`的优先级：1 + 1 = 2

**参考**

1. [https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity)

## CSS 里面的`id`和`class`有什么区别？

* `id`：唯一的元素标识，一个元素只允许有一个`id`属性。一般用于获取DOM元素，也可以作为页面 url 的 hash 以便于跳转时直接展示该元素（比如`http://abcblog.com/foo#123`这个网址会打开页面时自动展示`id="123"`的元素）。
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

说到浮动就不得不提到**清除浮动**，因为浮动通常会带来一些副作用，最常见的就是如果父元素的所有子元素都是浮动的，那么其高度就会变为 0。

清除浮动的方法主要有：

* 设置`clear`属性。
* 兼容大部分浏览器的`clearfix`，把`clear`属性写在`::after`伪元素，避免直接改写内容元素。
* 触发 BFC 的方式来清除浮动。比如`overflow: auto`，或者`overflow: hidden`

**参考**

1. [http://www.w3school.com.cn/css/css_positioning_floating.asp](http://www.w3school.com.cn/css/css_positioning_floating.asp)

## `z-index`和层叠上下文

当元素出现重叠时，`z-index`属性用于决定层级（通常来说`z-index`较大的元素会覆盖较小的一个）。对于一个已经定位的元素，设置`z-index`会：

1. 指定元素当前层叠上下文的层级
2. 决定是否创建新的本地层叠上下文

如果不指定`z-index`，那么就按照 DOM 结构的顺序（下面的元素会遮盖上面），但已定位的元素会始终在普通元素上方。

层叠上下文是一种三维概念，指元素在面向用户的方向上（Z 轴）会根据自身属性按照优先级会分为很多层，然后进行堆叠。

在层叠上下文中，子元素的`z-index`值相对于本地上下文，并且与外部的其他元素独立。举个例子：元素 A 前面有一个兄弟元素 B，A 有一个子元素 C，那么即使 C 设置的`z-index`更高，也不会覆盖 B 元素。

层叠上下文堆叠的顺序是先内再外，即当元素的内容层叠完毕之后，再按照元素的层级插入到父级的层叠上下文中。

文档中的层叠上下文由满足下列条件的元素形成（常见的）：

* 根元素（`<html>`）
* `z-index`不为`auto`的绝对定位、相对定位、flex-item 元素
* `position: fixed`的元素
* `opacity`小于 1 的元素
* `transform`、`filter`、`perspective`不为`none`的元素

**参考**

1. [https://developer.mozilla.org/zh-CN/docs/Web/CSS/z-index](https://developer.mozilla.org/zh-CN/docs/Web/CSS/z-index)
2. [https://css-tricks.com/almanac/properties/z/z-index/](https://css-tricks.com/almanac/properties/z/z-index/)
3. [https://philipwalton.com/articles/what-no-one-told-you-about-z-index/](https://philipwalton.com/articles/what-no-one-told-you-about-z-index/)
4. [https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)

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

* 减小 HTTP 请求次数（HTTP2 多路复用的特性，不再有并发限制，所以不会存在此问题）

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

## 使用 CSS 预处理器的优点

优点：

* CSS 可维护性更好
* 嵌套选择器写起来更方便
* 可以定义使用变量
* 使用混入（mixin）的方式实现代码复用
* 将 CSS 分为更多文件（使用`@import`的方式本就可以讲 CSS 分为多个文件，但是会造成更多的 HTTP 请求）

## 如何在网页中使用非标准的字体

使用`@font-face`下载该字体，并定义`font-family`和`font-weight`。

## 描述下浏览器如何将元素匹配到相应的选择器规则

在上面有效的 CSS 问题中已经说过，浏览器时从右到左进行匹配：首先通过最右的关键选择器过滤元素，然后向其祖先元素遍历看是否符合规则。

例如对于选择器`p span`，浏览器会首先找到所有的`<span>`元素，然后向祖先元素进行遍历，查找`<p>`元素。一旦找到存在，就视为符合选择器并会立刻停止继续向上遍历。

## 描述下盒模型

浏览器在对页面中的元素进行布局时，每一个元素会被视为一个矩形的盒子，每个盒子包括：内容，内边距，边框，外边距。

盒模型用于：

1. 一个元素占据的位置
2. 边框和外边距是否折叠
3. 盒子的尺寸

盒模型尺寸计算公式：内容 + 内边距 + 边框 + 外边距

另外，CSS 中的`width`和`height`默认设置的是内容的宽高，可以通过`box-sizing`设置。

**参考**

1. [https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)

## `* { box-sizing: border-box; }`是干什么的？有什么好处？

设置所有元素的`box-sizing`，改变元素`width`和`height`的计算方式。该属性的默认值是`content-box`，即盒子的宽高（width`和`height`属性）是盒子内容的宽高；而设置为`border-box`之后，变为盒子内容 + 内边距 + 边框。

好处就是，改变所有元素尺寸的计算方式，简化盒子尺寸的计算方式。因为盒子占据的空间会对布局有影响，尤其是元素存在内边距和边框时，导致设置元素的`width`和`height`需要额外的计算（尤其是宽度百分比，`padding`固定的情况）。

## 描述下`block`，`inline`，`inline-block`的区别

|                      | block                             | inline                     | inline-block     |
| -------------------- | --------------------------------- | -------------------------- | ---------------- |
| **尺寸**             | 宽度是容器的 100%，高度是内容决定 | 由内容决定                 | 由内容决定       |
| **位置**             | 自己独占一行                      | 与其他元素同一行           | 与其他元素同一行 |
| **设置宽高**         | 是                                | 否                         | 是               |
| **`vertical-align`** | 否                                | 是                         | 是               |
| **设置内外边距**     | 是                                | 只有水平方向的内外边距有效 | 是               |
| **浮动**             | -                                 | 浮动后可以设置内外边距     | -                |

## 都有哪些定位的属性，分别有什么不同？

元素定位通过`position`属性设置，包括`static`（默认值），`relative`，`absolute`和`fixed`，后三种属性的元素又称为已定位元素，可以使用`top`，`left`，`bottom`，`right`设定元素位置（如果不设置，就会在原来文档流中的位置）；可以使用`z-index`设定元素层级。

* `static`：元素默认的定位方式，即普通文档流中的位置。此时设置`top`，`left`，`bottom`，`right`和`z-index`不起作用。
* `relative`：相对定位，相对于自身原来进行偏离；元素占据的位置仍然在普通文档流中。
* `absolute`：绝对定位，相对于已经定位的祖先元素进行定位；元素脱离文档流；元素宽高默认内容决定。
* `fixed`：固定定位，相对于视窗进行定位，不随页面滚动而改变；元素脱离文档流；元素宽高默认内容决定。

**提示**

已经为元素除了可以使用`width`和`height`设置其宽高外，还可以同时指定`left`和`right`，`top`和`bottom`分别设置宽和高。

**参考**

1. [https://developer.mozilla.org/zh-CN/docs/Web/CSS/position](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position)

## 有接触过 CSS`flex`布局以及栅格布局么？

了解过`flex`布局，但是没有熟悉到每一个属性的作用以及写法。其优点就是功能强大，就像布局的一颗银弹，可以几乎适应所有的布局方式（固定宽度，自适应宽度，垂直排列，多栏布局。。。）。但其最大的缺点就是兼容性。

栅格布局就是提前将网页分割为多个栅格（一般是 12），然后再通过设置元素占据的栅格数来布局。优点是适用于所有设备，兼容性较好，如广为人知的 Bootstrap。但栅格说白了就是百分比布局，所以不适用于所有布局情况。

## 响应式（responsive）和自适应（adaptive）有什么区别？

首先这两种技术的目的都是能够在不同设备、不同分辨率下都得到非常好的显示效果。

响应式通过`media query`、栅格、百分比、rem 等技术，让网页在任何设备上达到最好的显示效果。

自适应则更像是渐进式增强，通过获取当前设备的特征，然后设置预定义的视图大小和其他特性，提供合适的功能和布局。

**参考**

1. [https://css-tricks.com/the-difference-between-responsive-and-adaptive-design/](https://css-tricks.com/the-difference-between-responsive-and-adaptive-design/)

## 相比于使用`absolute`定位，使用`translate()`有哪些好处？

`translate()`和`opacity`不会引起浏览器的重绘以及重排。浏览器只会重新组合（composition）。但是改变绝对定位元素的位置会造成重绘。所以使用`translate()`的方式性能更高。
