# HTML 相关问题

  - [`DOCTYPE`是干啥的？](#doctype%E6%98%AF%E5%B9%B2%E5%95%A5%E7%9A%84%EF%BC%9F)
  - [如果页面中存在多种语言，应该如何处理？](#%E5%A6%82%E6%9E%9C%E9%A1%B5%E9%9D%A2%E4%B8%AD%E5%AD%98%E5%9C%A8%E5%A4%9A%E7%A7%8D%E8%AF%AD%E8%A8%80%EF%BC%8C%E5%BA%94%E8%AF%A5%E5%A6%82%E4%BD%95%E5%A4%84%E7%90%86%EF%BC%9F)
  - [在设计或开发多语言站点时，必须注意哪些事项？](#%E5%9C%A8%E8%AE%BE%E8%AE%A1%E6%88%96%E5%BC%80%E5%8F%91%E5%A4%9A%E8%AF%AD%E8%A8%80%E7%AB%99%E7%82%B9%E6%97%B6%EF%BC%8C%E5%BF%85%E9%A1%BB%E6%B3%A8%E6%84%8F%E5%93%AA%E4%BA%9B%E4%BA%8B%E9%A1%B9%EF%BC%9F)
  - [使用`data-`属性有什么好处？](#%E4%BD%BF%E7%94%A8data-%E5%B1%9E%E6%80%A7%E6%9C%89%E4%BB%80%E4%B9%88%E5%A5%BD%E5%A4%84%EF%BC%9F)
  - [描述 cookie，sessionStorage 和 localStorage 之间的区别](#%E6%8F%8F%E8%BF%B0-cookie%EF%BC%8Csessionstorage-%E5%92%8C-localstorage-%E4%B9%8B%E9%97%B4%E7%9A%84%E5%8C%BA%E5%88%AB)
  - [描述`<script>`，`<script async>`和`<script defer>`之间的区别](#%E6%8F%8F%E8%BF%B0script%EF%BC%8Cscript-async%E5%92%8Cscript-defer%E4%B9%8B%E9%97%B4%E7%9A%84%E5%8C%BA%E5%88%AB)
  - [为什么 CSS 的`<link>`要放在`<head>`中，而 JS 文件`<script>`放在`<body>`最后？有例外情况么？](#%E4%B8%BA%E4%BB%80%E4%B9%88-css-%E7%9A%84link%E8%A6%81%E6%94%BE%E5%9C%A8head%E4%B8%AD%EF%BC%8C%E8%80%8C-js-%E6%96%87%E4%BB%B6script%E6%94%BE%E5%9C%A8body%E6%9C%80%E5%90%8E%EF%BC%9F%E6%9C%89%E4%BE%8B%E5%A4%96%E6%83%85%E5%86%B5%E4%B9%88%EF%BC%9F)
  - [什么是渐进式渲染？](#%E4%BB%80%E4%B9%88%E6%98%AF%E6%B8%90%E8%BF%9B%E5%BC%8F%E6%B8%B2%E6%9F%93%EF%BC%9F)
  - [你有用过哪些 HTML 模板语言？](#%E4%BD%A0%E6%9C%89%E7%94%A8%E8%BF%87%E5%93%AA%E4%BA%9B-html-%E6%A8%A1%E6%9D%BF%E8%AF%AD%E8%A8%80%EF%BC%9F)
  - [其他问题](#%E5%85%B6%E4%BB%96%E9%97%AE%E9%A2%98)

## `DOCTYPE`是干啥的？

`DOCTYPE`是文档类型的缩写，是 HTML5 中用来区分**标准兼容模式**、**怪异模式**的声明，告诉浏览器用标准兼容模式解析并渲染文档。

> 提示：只要在你文档的最前面添加`<!DOCTYPE html>`就可以了。

**参考**：

1. [https://stackoverflow.com/questions/7695044/what-does-doctype-html-do](https://stackoverflow.com/questions/7695044/what-does-doctype-html-do)
2. [https://www.w3.org/QA/Tips/Doctype](https://www.w3.org/QA/Tips/Doctype)

## 如果页面中存在多种语言，应该如何处理？

这个问题本身就有点问题，因为大多数情况下页面应该仅显示一种语言。

当客户端发送一个 HTTP 请求到服务器时，通常会携带关于语言的设定，比如`Accept-Language`请求头，这样服务器就可以返回相应语言的文档，并且返回的 HTML 文档应该声明相同的`lang`属性，如`<html lang="zh-cn"> ... </html>`。

**参考**：

1. [https://www.w3.org/International/getting-started/language](https://www.w3.org/International/getting-started/language)

## 在设计或开发多语言站点时，必须注意哪些事项？

* 使用`lang`属性。
* 引导用户使用母语：允许用户毫不费力地改变他的国家/语言。
* 使用图像代替文字：使用图片可以获得更好看以及在任何电脑上获得相同的效果，但是需要对不同语言分别使用不同图片。
* 限制词语/语句长度：一些语句翻译成其他语言之后可能会变长，设计与布局的时候需要注意，避免破坏布局。通常出现在标题栏，标签，按钮等元素中。
* 注意颜色的使用：不同文化中颜色的意义不同。
* 时间和货币格式化：不同地区的显示方式不同。
* 注意语句顺序：千万不要这么做：`"The date today is " + date`，不同语言中会出现不同的断句，改用模板参数代替。
* 语言阅读方向：大多数语言都是从左到右，但在古代汉语中是从右到左。

**参考**：

1. [https://www.quora.com/What-kind-of-things-one-should-be-wary-of-when-designing-or-developing-for-multilingual-sites](https://www.quora.com/What-kind-of-things-one-should-be-wary-of-when-designing-or-developing-for-multilingual-sites)

## 使用`data-`属性有什么好处？

在 JS 框架流行之前，前端工程师们都是用`data-`属性将存储额外的数据存储在 DOM 中，或者其他非标准属性。

但是时至今日并不推荐使用`data-`属性了，因为：

1. 用户可以轻易的修改 DOM 上的数据属性
2. 数据模型的改变也不宜追踪。

所以更好的方式是将数据模型存储在 JS 中然后使用某个库或框架与 DOM 节点进行绑定。

**参考**：

1. [http://html5doctor.com/html5-custom-data-attributes/](http://html5doctor.com/html5-custom-data-attributes/)
2. [https://www.w3.org/TR/html5/dom.html#embedding-custom-non-visible-data-with-the-data-\*-attributes](https://www.w3.org/TR/html5/dom.html#embedding-custom-non-visible-data-with-the-data-*-attributes)

## 描述 cookie，sessionStorage 和 localStorage 之间的区别

以上三种都是以键值对形式在客户端存储数据用的技术，并且值的形式只能是字符串。

|                  | cookie         | sessionStorage | localStorage |
| ---------------- | -------------- | -------------- | ------------ |
| **发起者**       | 客户端，服务端 | 客户端         | 客户端       |
| **过期时间**     | 手动设置       | 会话期间       | 永久         |
| **跨浏览器会话** | 由过期时间决定 | 否             | 是           |
| **域名相关**     | 是             | 否             | 否           |
| **请求携带**     | 是             | 否             | 否           |
| **大小限制**     | 4kb            | 5MB            | 5MB          |
| **可访问性**     | 任何窗口       | 同一个 tab     | 任何窗口     |

**参考**：

1. [https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
2. [http://tutorial.techaltum.com/local-and-session-storage.html](http://tutorial.techaltum.com/local-and-session-storage.html)

## 描述`<script>`，`<script async>`和`<script defer>`之间的区别

* `<script>`：阻塞 HTML 的解析，等待 js 文件加载并执行完毕之后才会继续。
* `<script async>`：js 文件下载与 HTML 解析并行执行，并在下载完成之后立即执行（有可能在 HTML 解析之前发生）。最佳实践：当该 js 文件与页面中其他 js 文件无关时使用`async`，比如统计类功能。
* `<script defer>`：js 文件下载与 HTML 解析并行执行，但在 HTML 解析完成之后执行。如果存在多个，则按照文档中的顺序进行执行。适合于一个 js 文件对完全渲染后的 DOM 有依赖的情况。PS：基本上这种 js 文件与防止带`<body>`最后的 js 文件没有区别；延迟的 js 文件禁止使用`document.write`。

> 注意：如果`<script>`中没有`src`属性，`async`和`defer`属性也会被忽略。

**参考**：

1. [http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html](http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html)
2. [https://stackoverflow.com/questions/10808109/script-tag-async-defer](https://stackoverflow.com/questions/10808109/script-tag-async-defer)
3. [https://bitsofco.de/async-vs-defer/](https://bitsofco.de/async-vs-defer/)

## 为什么 CSS 的`<link>`要放在`<head>`中，而 JS 文件`<script>`放在`<body>`最后？有例外情况么？

**`<link>`放在`<head>`中**

这是一种规范，此外 CSS 文件会阻塞渲染，所以应该尽早的进行加载以便更快的展示带有样式的页面。

将 CSS 文件放置在 body 中会造成：

* 一些浏览器不会解析该文件，比如 IE。
* 可能造成 CSS 文件之前的 DOM 节点重绘（repaint）或回流（reflow）。
* 可能造成无样式刷新。即用户首先看到了没有样式的页面，而当 CSS 下载好之后，再重新渲染。

**`<script>`放在`<body>`最后**

`<script>`标签的下载和执行会阻塞 HTML 的解析，所以放在`<body>`最后可以将解析完成元素先展示出来。

唯一的例外就是：当你的代码包括`document.write()`（但是最好别这么干 🙅‍♂️）

> 重要知识点！！！
>
> 1. 浏览器解析 HTML 文档为 DOM 树，解析 CSS 文件生成 CSSOM 树，二者合并为渲染树（并不是只有 DOM 树构建完毕了才会去生成渲染树的）。
> 2. 现在的浏览器非常聪明，会在解析 HTML 的一开始就发出所有可能的请求（CSS，JS，图片：发送的顺序与在 HTML 的顺序一致）。
> 3. CSS 的解析会阻塞渲染树的生成。
> 4. JS 的下载和执行均会阻塞 HTML 解析。
> 5. JS 的执行依赖于最新的 CSSOM 结果，即 CSS 解析会阻塞 JS 执行。

所以，结合上面的 3，4，5，我们要：

1. 尽早的下载 CSS 文件（放在`<head>`里面），并尽可能减小其大小;
2. 最好给`<script>`标签添加`defer`和`async`属性避免阻塞；
3. 如果`<script>`标签不添加异步属性，也要最好放置在`<body>`最后，这样的话：即使其阻塞了后续 HTML 的解析，但由于后面并没有可渲染内容，所以只要是 CSSOM 树已经构建完毕了（上面的第一条原则也是为了早点下载，早点构建 CSSOM），JS 也没有在执行的话，直接根据当前的渲染树进行布局（Layout）并绘制（Paint），即不会阻止页面渲染！

**参考**：

1. [https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp)

## 什么是渐进式渲染？

渐进式渲染是一项尽快渲染网页内容，从而提高网页性能（其实是降低感知上的加载时间）的技术。并且移动互联网的兴起，其依然非常重要。

比如这些技术：

* 图片懒加载：网页中的图片不会一次性全部加载，而是当图片出现在设备视窗中之后才去加载。
* 局部加载：首次打开页面的时候仅加载最基本的 CSS、内容、JS 来降低等待时间，然后在利用推迟加载的 JS 加载剩余内容。

**参考**：

1. [https://stackoverflow.com/questions/33651166/what-is-progressive-rendering](https://stackoverflow.com/questions/33651166/what-is-progressive-rendering)

## 你有用过哪些 HTML 模板语言？

个人用过的有 EJS、Handlebars、Freemarker、Velocity、ArtTemplate

## 其他问题

* [https://neal.codes/blog/front-end-interview-questions-html/](https://neal.codes/blog/front-end-interview-questions-html/)
* [http://peterdoes.it/2015/12/03/a-personal-exercise-front-end-job-interview-questions-and-my-answers-all/](http://peterdoes.it/2015/12/03/a-personal-exercise-front-end-job-interview-questions-and-my-answers-all/)
