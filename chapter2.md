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

