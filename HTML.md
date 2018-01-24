## `doctype`是干啥的？

`doctype`是文档类型的缩写，是HTML5中用来区分**标准兼容模式**、**怪异模式**的声明，告诉浏览器用标准兼容模式解析并渲染文档。

> 提示：只要在你文档的最前面添加`<!DOCTYPE html>`就可以了。

**参考**：

1. [https://stackoverflow.com/questions/7695044/what-does-doctype-html-do](https://stackoverflow.com/questions/7695044/what-does-doctype-html-do)
2. [https://www.w3.org/QA/Tips/Doctype](https://www.w3.org/QA/Tips/Doctype)

## 如果页面中存在多种语言，应该如何处理？

这个问题本身就有点问题，因为大多数情况下页面应该仅显示一种语言。

当客户端发送一个HTTP请求到服务器时，通常会携带关于语言的设定，比如`Accept-Language`请求头，这样服务器就可以返回相应语言的文档，并且返回的HTML文档应该声明相同的`lang`属性，如`<html lang="zh_CN"> ... </html>`。

**参考**：

1. [https://www.w3.org/International/getting-started/language](https://www.w3.org/International/getting-started/language)

## 在设计或开发多语言站点时，必须注意哪些事项？

- 使用`lang`属性。
- 引导用户使用母语：允许用户毫不费力地改变他的国家/语言。
- 使用图像代替文字：使用图片可以获得更好看以及在任何电脑上获得相同的效果，但是需要对不同语言分别使用不同图片。
- 限制词语/语句长度：一些语句翻译成其他语言之后可能会变长，设计与布局的时候需要注意，避免破坏布局。通常出现在标题栏，标签，按钮等元素中。
- 注意颜色的使用：不同文化中颜色的意义不同。
- 时间和货币格式化：不同地区的显示方式不同。
- 注意语句顺序：千万不要这么做：`"The date today is " + date`，不同语言中会出现不同的断句，改用模板参数代替。
- 语言阅读方向：大多数语言都是从左到右，但在古代汉语中是从右到左。

**参考**：

1. [https://www.quora.com/What-kind-of-things-one-should-be-wary-of-when-designing-or-developing-for-multilingual-sites](https://www.quora.com/What-kind-of-things-one-should-be-wary-of-when-designing-or-developing-for-multilingual-sites)

## 使用`data-`属性有什么好处？

在JS框架流行之前，前端工程师们都是用`data-`属性将存储额外的数据存储在DOM中，或者其他非标准属性。

但是时至今日并不推荐使用`data-`属性了，因为：

1. 用户可以轻易的修改DOM上的数据属性
2. 数据模型的改变也不宜追踪。

所以更好的方式是将数据模型存储在JS中然后使用某个库或框架与DOM节点进行绑定。

**参考**：

1. [http://html5doctor.com/html5-custom-data-attributes/](http://html5doctor.com/html5-custom-data-attributes/)
2. [https://www.w3.org/TR/html5/dom.html#embedding-custom-non-visible-data-with-the-data-*-attributes](https://www.w3.org/TR/html5/dom.html#embedding-custom-non-visible-data-with-the-data-*-attributes)

## 描述cookie，sessionStorage和localStorage之间的去区别

以上三种都是以键值对形式在客户端存储数据用的技术，并且值的形式只能是字符串。

|               |cookie        |sessionStorage    |localStorage    |
|---------------|--------------|------------------|----------------|
|**发起者**      |客户端，服务端  |客户端            |客户端           |
|**过期时间**    |手动设置        |会话期间          |永久             |
|**跨浏览器会话** |由过期时间决定  |否               |是               |
|**域名相关**    |是             |否                |否               |
|**请求携带**    |是             |否                |否               |
|**大小限制**    |4kb            |5MB               |5MB             |
|**可访问性**    |任何窗口        |同一个tab         |任何窗口         |


**参考**：

1. [https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
2. [http://tutorial.techaltum.com/local-and-session-storage.html](http://tutorial.techaltum.com/local-and-session-storage.html)

## 描述`<script>`，`<script async>`和`<script defer>`之间的区别

- `<script>`：阻塞HTML的解析，等待js文件加载并执行完毕之后才会继续。
- `<script async>`：js文件下载与HTML解析并行执行，并在下载完成之后立即执行（有可能在HTML解析之前发生）。最佳实践：当该js文件与页面中其他js文件无关时使用`async`，比如统计类功能。
- `<script defer>`：js文件下载与HTML解析并行执行，但在HTML解析完成之后执行。如果存在多个，则按照文档中的顺序进行执行。适合于一个js文件对完全渲染后的DOM有依赖的情况。PS：基本上这种js文件与防止带`<body>`最后的js文件没有区别；延迟的js文件禁止使用`document.write`。

> 注意：如果`<script>`中没有`src`属性，`async`和`defer`属性也会被忽略。

**参考**：

1. [http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html](http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html)
2. [https://stackoverflow.com/questions/10808109/script-tag-async-defer](https://stackoverflow.com/questions/10808109/script-tag-async-defer)
3. [https://bitsofco.de/async-vs-defer/](https://bitsofco.de/async-vs-defer/)

## 为什么CSS的`<link>`要放在`<head>`中，而JS文件`<script>`放在`<body>`最后？有例外情况么？

**`<link>`放在`<head>`中**

这是一种规范，此外CSS文件会阻塞渲染，所以应该尽早的进行加载以便更快的展示带有样式的页面。

将CSS文件放置在body中会造成：

- 一些浏览器不会解析该文件，比如IE。
- 可能造成CSS文件之前的DOM节点重绘（repaint）或回流（reflow）。
- 可能造成无样式刷新。即用户首先看到了没有样式的页面，而当CSS下载好之后，再重新渲染。

**`<script>`放在`<body>`最后**

`<script>`标签的下载和执行会阻塞HTML的解析，所以放在`<body>`最后可以将上面的解析完成之后的HTML先展示出来。


有一个例外，就是当你的代码包括`document.write()`的情况。

> 提示：由于`<script>`标签会被CSSOM树和渲染树忽略，所以解析到放在`<body>`最后的`<script>`时，如果CSSOM树已经构建完毕，那么渲染树那就直接先渲染！