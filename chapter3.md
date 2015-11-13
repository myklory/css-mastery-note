# 可视化格式模型

###**1. 盒子模型**

详细的盒子模型可以参考

* [【原创翻译】深入理解CSS盒子模型](http://www.cnblogs.com/hh54188/archive/2010/12/28/1919078.html)
* [CSS 框模型概述](http://www.w3school.com.cn/css/css_boxmodel.asp)
* [CSS box-flex属性，然后弹性盒子模型简介](http://www.zhangxinxu.com/wordpress/2010/12/css-box-flex%E5%B1%9E%E6%80%A7%EF%BC%8C%E7%84%B6%E5%90%8E%E5%BC%B9%E6%80%A7%E7%9B%92%E5%AD%90%E6%A8%A1%E5%9E%8B%E7%AE%80%E4%BB%8B/)
* [详解css3弹性盒模型（Flexbox）](http://segmentfault.com/a/1190000000707526)

盒子模型示意图如下：

![box-model](http://7xo9fs.com1.z0.glb.clouddn.com/022345511601591.jpg)

从图中可以看出，元素的width,height只是元素的高宽，并不包含margin和padding。

####**1.1 外边距叠加**

* 当一个元素出现在另一个元素上面时，上面元素的底外边距与下面元素的顶外边距发生叠加，新的外边距高度等于两个发生叠加的外边距的高度中的较大者

![margin](http://7xo9fs.com1.z0.glb.clouddn.com/20151112162223.png)

* 当一个元素包含在另一个元素中时（假设没有内边距或边框将外边距分隔开），它们的顶和/或底外边距也会发生叠加

![margin](http://7xo9fs.com1.z0.glb.clouddn.com/20151112162645.png)

* 当一个空元素，它有外边距，但是没有边框或内边距，在这种情况下，顶外边距和底外边距就会发生叠加

![margin](http://7xo9fs.com1.z0.glb.clouddn.com/20151112162656.png)

* 如果这个外边距碰到另一个元素的外边距，还会发生叠加

![margin](http://7xo9fs.com1.z0.glb.clouddn.com/20151112162708.png)

**只有普通文档流中块框的垂直外边距才会发生外边距叠加。行内框、浮动框或绝对定位框之间的外边距不会叠加。**

###**2. 定位**
####**2.1 可视化格式模型**
p、h1或div等元素称为块级元素，意味着这些元素显示为一块内容，即“块框”。

strong和span等元素称为行内元素，它们的内容显示在行中，即“行内框”。

可以使用display属性改变生成的框的类型。通过将display属性设置为block可以将行内元素表现得像块级元素一样。还可以通过将display属性设置为none，让生成的元素没有框，即框及其所有内容都不显示，不占用文档的空间。

CSS中有3种基本的定位机制：普通流、浮动和绝对定位。默认所有框都在普通流中定位。普通流中的元素框的位置由元素在HTML中的位置决定。

块级框从上到下垂直排列，行内框水平排列。

关于行内元素的高可参考[css行高line-height的一些深入理解及应用](http://www.zhangxinxu.com/wordpress/2009/11/css%E8%A1%8C%E9%AB%98line-height%E7%9A%84%E4%B8%80%E4%BA%9B%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E5%8F%8A%E5%BA%94%E7%94%A8/)
####**2.2 相对定位**
相对定位是相对于元素原来的位置移动一定的位置，在使用相对定位时，无论是否移动，元素仍然占据原来的空间，因此，移动会导致它覆盖其他框。
```css 
#myBox {
  position: relative;
  left: 20px;
  top: 20px;
}
```

####**2.3 绝对定位**
绝对定位的元素位置是相对于距离它最近的那个已定位的祖先元素确定的，如果没有已定位的祖先元素，那么它的位置是相对于初始包含块。祖先元素需要使用相对定位先定位
```cs
#branding {
  width: 70em;
  height: 10em;
  position: relative;
}
#branding .tel {
  position: absolute;
  right: 1em;
  bottom: 1em;
  text-align: right;
}
```
```html
<div id="branding">
  <p class="tel">Tel:123455</p>
</div>
```
####**2.4 固定定位**
固定定位类似于绝对定位，但是它的包含块是viewport，即我们总是能够看见使用绝对定位的元素。
####**2.5 浮动**
浮动的框可以左右移动，直到它的外边缘碰到包含框或另一个浮动框的边缘。因为浮动框不在文档的普通流中，所以浮动框会覆盖原来位置的元素。如果包含块太窄，不能容纳水平排列的几个浮动元素，其它的浮动块向下移动，直到有足够的空间，如果浮动元素的高度不同，那么它们向下移动时可能被其他浮动元素止住。

更多的浮动和清除浮动内容参考：
* [那些年我们一起清除过的浮动](http://www.iyunlu.com/view/css-xhtml/55.html)
* [清理浮动的那些事儿](http://lightcss.com/all-about-clear-float/#toc-35)
* [CSS浮动](http://www.cnblogs.com/zhongxinWang/archive/2013/03/27/2984764.html)
* [css-float浮动的深入研究、详解及拓展一](http://www.zhangxinxu.com/wordpress/2010/01/css-float%E6%B5%AE%E5%8A%A8%E7%9A%84%E6%B7%B1%E5%85%A5%E7%A0%94%E7%A9%B6%E3%80%81%E8%AF%A6%E8%A7%A3%E5%8F%8A%E6%8B%93%E5%B1%95%E4%B8%80/)
