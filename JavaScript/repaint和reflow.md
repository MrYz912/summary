# 1.重绘(repaint)

由于节点的几何属性或样式发生改变而不影响布局的，就是重绘，例如`outline`, `visibility`, `color`, `backgroud-color`等。



# 2.回流(reflow)

回流是布局发生改变，是影响浏览器性能的关键因素，因为其变化涉及部分页面甚至整个页面布局更新



# 3.浏览器优化

大多数通过队列来批量更新布局，浏览器会将修改操作放在队列里，至少一个浏览器刷新（16.6ms）才会清空队列，但获取布局信息时，浏览器会强制清空队列

主要包括以下方法和属性：

- `offsetTop`、`offsetLeft`、`offsetWidth`、`offsetHeight`
- `scrollTop`、`scrollLeft`、`scrollWidth`、`scrollHeight`
- `clientTop`、`clientLeft`、`clientWidth`、`clientHeight`
- `width`、`height`
- `getComputedStyle()`
- `getBoundingClientRect()`

尽量避免频繁使用上述属性



# 4.减少重绘和回流

## 1.CSS

- **使用 `transform` 替代 `top`**
- **使用 `visibility` 替换 `display: none`** ，因为前者只会引起重绘，后者会引发回流（改变了布局
- **避免使用`table`布局**，可能很小的一个小改动会造成整个 `table` 的重新布局。
- **尽可能在`DOM`树的最末端改变`class`**，回流是不可避免的，但可以减少其影响。尽可能在DOM树的最末端改变class，可以限制了回流的范围，使其影响尽可能少的节点。
- **避免设置多层内联样式**，CSS 选择符**从右往左**匹配查找，避免节点层级过多。

- **将动画效果应用到`position`属性为`absolute`或`fixed`的元素上。**

- **将频繁重绘或者回流的节点设置为图层**

- **CSS3 硬件加速（GPU加速）**



## 2.JavaScript

- **避免频繁操作样式**，最好一次性重写`style`属性，或者将样式列表定义为`class`并一次性更改`class`属性。
- **避免频繁操作`DOM`**，创建一个`documentFragment`，在它上面应用所有`DOM操作`，最后再把它添加到文档中。
- **避免频繁读取会引发回流/重绘的属性**，如果确实需要多次使用，就用一个变量缓存起来。
- **对具有复杂动画的元素使用绝对定位**，使它脱离文档流，否则会引起父元素及后续元素频繁回流。





