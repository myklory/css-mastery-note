# 为样式找到应用目标

###**1.选择器**
####**1.1元素选择器**
元素选择器也叫一般选择器。
```css
p { color: black; }
h1 { font-size: 16px; font-weight: bold; }
```

####**1.2 后代选择器**
后代选择器由空格进行分隔，在这个示例中只缩进是块引用的后代的段落元素，其它段落不受影响。
```css
blockquote p { padding-left: 2em; }
```

####**1.3 ID选择器**
ID选择器以#开头
```css
#intro { font-weight: bold; }
```
```html
<p id="intro">ID selector</p>
```
####**1.4 类选择器**
类选择器以.开头
```css
.date { color: #ccc; }
```
```html
<p class="date">Class selector</p>
```
####**1.5 伪类选择器**
```css
/*设置未访问的连接为blue*/
a:link { color: blue; }
/*设置已访问的连接为绿色*/
a:visited { color: green; }
/*设置当前指向，激活连接时为红色，键盘焦点在连接时也为红色*/
/*以逗号分隔的格式表示多个选择器使用相同的设置*/
a:hover, a:focus, a:active { color: red; }
/*鼠标指针指向表格行时背景色为红色*/
tr:hover { background-color: red; }
/*当输入框为焦点时设置背景色为黄色*/
input:focus { background-color: red; }
```
:link和:visited称为链接伪类，只能用于链接。:hover, :focus, :active称为动态伪类，理论上可用于任何元素。

####**1.6 通用选择器**
通用选择器可应用到所有的元素上,强大而最不常用。
```css
* {
  margin: 0;
  padding: 0;
}
```

####**1.7 子选择器**
子选择器只选择元素的直接后代，不选择孙后代。后代选择器选择所有后代。
```css
#nav>li { color: yellow; }
```
```html
<ul id="nav">
  <li>this font color is yellow.</li>
  <li>this font color is yellow too.
    <ul>
      <li>this font color is default</li>
    </ul>
  </li>
</ul>
```
####**1.8 相邻同胞选择器
下面的选择器只应用于紧临h2，且与h2同级的p元素。
```css
h2 + p { color: red; }
```
```html
<h2>this is h2</h2>
<p>this color is red.</p>
<p>this color is default.</p>
```
####**1.9 属性选择器**
下面例子将有title属性的p元素加上点下划线。
```css
p[title] { border-bottom: 1px, dotted, #999; }
```
下面例子将title属性值为head的p元素设置为红色。
```css
p[title="head"] { color: red; }
```
###**2. 特殊性**
特殊性分为a,b,c,d4个等级
* 如果样式是行类样式，a=1
* b等于ID选择器的总数
* c等于类，伪类，属性选择器的总数
* d等于类型选择器和伪元素选择器的总数

