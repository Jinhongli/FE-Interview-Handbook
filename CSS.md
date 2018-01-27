## 描述一下CSS选择器的优先级

浏览器在计算一个元素的CSS规则时，当多个选择器出现冲突时，就会根据CSS选择器的优先级来决定。CSS选择器的优先级从高到低，分别是：

1. ID选择器（`#example`）
2. 类选择器（`.example`），属性选择器（`[type="text"]`），伪类选择器（`:hover`）
3. 元素选择器（`div`），伪元素选择器（`::before`）

计算CSS规则的方法：

* 把上面的优先级量化为十进制的数，从高到底分别是：100, 10, 1。然后在CSS规则中找到所有的选择器，然后将它们的优先级求和就是最终的结果。
* 通用选择器（`*`），连接符（`+`, `>`, `~`, ` `），否定伪类（`:not()`）对优先级没有影响（优先级最低），计算时可以忽略。
* 带有`!important`属性的优先级最高。
* 同优先级下，选择位置靠后的属性。

比如：
* `div#root`的优先级：100 + 1 = 101
* `p.red`的优先级：10 + 1 = 11
* `div p`的优先级：1 + 1 = 2

**参考**

1. [https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity)