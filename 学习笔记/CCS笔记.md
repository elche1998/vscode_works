# CCS
## 前言
```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
<style>
p.para1
{
	color:red;
    /*段落字体颜色是红色*/
	text-align:center;
    /*段落文字居中*/
} 
</style>
</head>

<body>
<p>Hello World!</p>
<p class="para1">这个段落采用CSS样式化。</p>
</body>
</html>
```
## 一、基本原理
### （一）样式表style
1. 样式表
   1. 外部样式表：`<head><link rel="stylesheet" type="text/css" href="mystyle.css"></head>`
   2. 内部样式表：`<head><style>p{color:red;}</style></head>`
   3. 内联样式：`<p style="color:red;">...</p>`
2. 优先级：内联样式 > 内部样式表 = 外部样式表 > 浏览器默认  
  * 如果外部样式放在内部样式的后面，则外部样式将覆盖内部样式。就是谁在后面，谁优先，通常是外部在前
### （二）选择器id，class（内部样式表为例）
1. id选择器(IS)
   ```html
   <style>
    #name{
      color:red;
    }
    </style>
    <!--下面文字是红色的-->
    <p id="name">red text</p>
   ```
2. class选择器(CS)（使用最多）：.前面也可以加某种元素（比如p.value），用来限制只有一种元素能用
    ```html
    <style>
    .value{
      text-align:center;
    }
    </style>
    <!--下面的文字是居中对齐的-->
    <p class="value">center text</p>
    ```
3. 元素(标签)选择器(ES)：默认的这种
  ```html
    <style>
    p{
      text-align:center;
    }
    </style>
    <!--下面的文字是居中对齐的-->
    <p>center text</p>
  ```
  * 包含选择器（PS）：`div p{color:yellow;}`，仅对div中的p有效(可以是子标签，孙标签...)。
  * 子选择器（SS）：`div>p{color:red;}`，只能套一层。
  * 兄弟选择器（BS）：同一层后面的应用。
    * 相邻兄弟：`div+p{color:red;}`，同一层匹配到div和p，则后面一个p使用该样式。
    * 后续兄弟：`div~p{color:red;}`，同一层匹配到div和p，则后面所有p使用该样式。
4. 优先级：内联样式 > id > class > 标签
5. 选择器的分组和嵌套
   1. 分组选择器：`h1,h2,p{color:green;}`
   2. 嵌套选择器：
      * `.marked p{}`: 为所有 class="marked" 元素内的 p 元素（如div里面的p）指定一个样式。
      * `p.marked{}`: 为所有 class="marked" 的 p 元素指定一个样式。
## 二、基本元素样式设置
### （一）背景background
1. 背景颜色：background-color
2. 背景图像：
   1. background-image（默认平铺），`body {background-image:url('paper.gif');}`
   2. background-repeat：设置平铺类型，x方向平铺repeat-x，不平铺no-repeat
   3. background-position：改变图像在背景中的位置，例如right top
   4. background-attachment：背景图片是否跟着页面滚动（默认scroll跟页面滚），fixed不滚，local跟元素滚
### （二）文本Text
1. 文本颜色(color)：＃FF0000，RGB(255,0,0)，red
2. 对齐方式(text-align)：center，right，justify（改变字间距，使每行对齐，好用）
3. 文本修饰(text-decoration)：none（可以用来去除链接的下划线），overline上划线，underline下划线，line-through删除线
4. 文本缩进：text-indent:50px
### （三）字体Fonts
1. 字体：
   1. 通用字体：serif，san-serif，monospace
   2. 特定字体：Times，Courier
2. 字体系列(font-family)：`p{font-family:"Times New Roman", Times, serif;}`不支持第一种，就选下一个。字体名称超过一个字（词）加引号。（详见Web安全字体组合）
3. 字体样式(font-style)：normal正常，italic斜体，oblique斜体（不推荐）
4. 字体大小(font-size)：16px=1em（后者兼容IE）
  * `<body>`元素的默认字体大小的是百分比，可以用它调节所有字体的大小
5. 简写：`font：font-style font-variant font-weight font-size/line-height font-family`
  * 例：`font:italic bold 12px/30px Georgia, serif;`
### （四）链接link
1. 链接样式
  ```css
  a:link {color:#000000;}      /* 未访问链接*/
  a:visited {color:#00FF00;}  /* 已访问链接 */
  a:hover {color:#FF00FF;}  /* 鼠标移动到链接上 */
  a:active {color:#0000FF;}  /* 鼠标点击时 */
  ```
  注：
  1. a:hover 必须跟在 a:link 和 a:visited后面。
  2. a:active 必须跟在 a:hover后面
2. 特性：
  * color，background-color
  * text-decoration：none/underline;（none可以删除下划线）
3. 创建链接框：display:block，padding（内边距） ，margin（外边距）
### （五）列表list
1. list-style-type：circle，square（无序）；upper-roman，lower-alpha（有序）
2. list-style-image（用图像做列表标记）: url('sqpurple.gif');
  * 浏览器兼容性解决方案
    ```css
    ul
    {
        list-style-type: none;
        padding: 0px;
        margin: 0px;
    }
    ul li
    {
        background-image: url(sqpurple.gif);
        background-repeat: no-repeat;
        background-position: 0px 5px; 
        padding-left: 14px; 
    }
    ```
3. 属性简写：list-style-type，position(inside/outside默认)，image
  例子：ul {list-style:square url("sqpurple.gif");}
### （六）表格table
* table表格，（tr是行），td是单元格，th是表头
* 一般先写`table, td, th{border:...}`，再写`th{...}`，`td{...}`
1. 表格边框(border)：`table,th,td {border:1px solid black;}`
2. 折叠边框（两条边框合成一条，重要！）：`border-collapse:collapse;`
3. 宽度和高度：width:100%; height:50px;
4. 文字对齐：text-align
5. 表格填充(td和th)：padding:15px
6. 表格颜色：文本和背景
## 三、盒子模型Box Model
1. 盒子模型
![](2020-08-08-09-56-58.png)
   1. margin：外边距
   2. border：边框
   3. padding：内边距
   4. content：内容
   * 总元素的宽度 = 内容宽度(width) + 左右填充(padding\*2) +左右边框(border\*2) + 左右边距(margin\*2)
   * 总元素的高度=内容高度(height) + 上下填充(padding\*2) +上下边框(border\*2) + 上下边距(margin\*2)
2. 边框border
   1. 边框样式(border-style)：none，dotted/dashed，solid
   2. 边框宽度(border-width)：2px，0.1em，thick/medium/thin
   3. 边框颜色(border-color)：name，RGB，Hex
   4. 单独设置各边：
      1. 分别设置`border-top/right/bottom/left-style:dotted;`
      2. 简便设置：`border-style:dotted solid double dashed;`上右下左，上(左右)下，(上下)(左右)
   5. 简写属性：`border:5px solid red;`
3. 轮廓outline：边框边缘的外围，可起到突出元素的作用（不占空间，不增加width和height），属性与边框类似。
4. 外边距margin：没有背景颜色，完全透明。
   1. 单独设置各边：`margin-top/right/bottom/left:100px;`
   2. 简写：`margin:25px 50px 75px 100px;`上右下左，上(左右)下，(上下)(左右)
5. 填充padding：内边距被清除时，所释放的区域将会受到元素背景颜色的填充（属性与margin基本相同）
   4. `padding-top/right/bottom/left:25px;`
   5. `padding:25px 50px 75px 100px;`上右下左，上(左右)下，(上下)(左右)注：文本先满足左边
## 四、CSS布局
1. 尺寸：height，width；min-width（最小宽度），max-width（最大宽度）
2. 显示：Display和Visibility
   1. 隐藏元素：
      1. 看不见但占空间：visibility:hidden;
      2. 看不见也不占空间：display:none;
   2. 改变元素显示（块和内联转换）：display:inline/block;
      * 块元素(block)：占全部宽度(h1,p,div,li)
      * 内联元素(inline)：不强制换行(span,a)
3. 定位(position)：具体位置用top，left设定到边缘的距离。
   1. static：默认，不特殊定位。后面跟坐标没用。
   2. relative：相对正常位置移动，可以有负值。
   3. fixed：相对浏览器窗口静止。
   4. absolute（重要）：位置相对于最近的已定位父元素，没有则相对于`<html>`。会和其他元素重叠。
   5. sticky：粘性定位，会跟着滚，但不会移出界面。(IE/Edge 15 及更早 IE 版本不支持 sticky 属性。 Safari 需要使用 -webkit，-prefix)
4. 滚动条(overflow)：元素溢出元素框
   1. visible：默认，不修剪内容，显示在框外。
   2. scroll：修剪，加滚动条
   3. hidden：修剪，其余内容看不到
   4. auto：自动处理，超了加滚动条
5. 浮动(float)：
   1. float（指定一个盒子是否可以浮动）：left/right
   2. clear（不允许元素周围有浮动元素）：left/right/both
6. 水平&垂直对齐
   1. 水平居中
      1. 元素居中（如div）：margin: auto;
      2. 文本居中：text-align: center;
      3. 图片居中：margin: auto;将它放倒块元素中
   2. 水平左右对齐
      1. 定位：position: absolute;right: 0px;
      2. 浮动：float: right;
         * 若子元素高度大于父元素，浮动就会溢出，在父元素上添加.clearfix{overflow: auto}来解决问题。
   3. 垂直居中
      1. padding:70px 0
      2. line-height（行高）： line-height与height相等 
      3. position和transform（？）：position: absolute;transform: translate(-50%, -50%);
## 五、CSS伪类和伪元素
1. 伪类(Pseudo-classes)：CSS类后面加"."，伪类后面加":"例如：`a:visited {color:#00FF00;}`
   1. 伪类可以和CSS类配合使用：`a.red:visited {color:#FF0000;}`
   2. :first-child伪类：`p:first-child{color:blue;}`，只有第一个`<p>`变蓝（匹配）。
   3. :lang伪类：为不同的语言定义特殊的规则
   4. :focus伪类：input:focus，鼠标点了，可以变颜色（等）
2. 伪元素(pseudo-element)：CSS类和伪类都能用
   1. :first-line：首行特殊设置，只能用于块级元素：`p:first-line{color:#ff0000;}`
   2. :first-letter：首字母特殊设置，只能用于块级元素：`p:first-letter{font-size:xx-large;}`
   3. :before：/:after，在元素前后插入新内容：`h1:before{content:url(smiley.gif);}`
   4. 补充
      1. 伪元素与CSS类：p.article:first-letter
      2. 可以有多个伪元素
## 六、实用组合招式
1. 导航栏：导航栏的实质是链接列表
   1. 垂直导航栏：ul+链接
   2. 水平导航栏：inline或者float（用后者）
2. 下拉菜单：任何元素都能打开下拉菜单
   1. div(dropdown) + button(dropbtn) + div(dropdown-content)
   2. dropdown-content隐藏（display:none），按一下button就出现(display:block)
3. 提示工具
4. 图片廊
   1. 图片透明/不透明
   2. 图片拼合
5. 媒体类型
6. 属性选择器
7. 表单
8. 计数器
## 七、网页布局

# CCS3

# CCS响应式设计