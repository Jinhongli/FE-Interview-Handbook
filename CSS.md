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

* [http://www.w3school.com.cn/css/css_positioning_floating.asp](http://www.w3school.com.cn/css/css_positioning_floating.asp)

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
2. [https://philipwalton.com/articles/what-no-one-told-you-about-z-index/](https://philipwalton.com/articles/what-no-one-told-you-about-z-index/)
3. [https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)
