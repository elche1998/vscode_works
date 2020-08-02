# HTML  
## 前言
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>春晓</h1>
    <p>春眠不觉晓</p>
    <hr>
</body>
</html>
```
快捷键：
* ！能初始化HTML  
* 写标签的时候，用tab键能自动补全  
* p*4生成四个p标签  
## 一、基础元素
1. 标题：`<h1>-<h6>`
2. 段落：
   * `<p>`
   * 折行：`<br>`==\n（空元素，没有关闭标签。`<br/>`更严谨）
3. 文本格式化：
   * 加粗：`<b>`或`<strong>`
   * 斜体：`<i>`或`<em>`
   * 放大：`<big>`
   * 缩小：`<small>`
   * 上标：`sup`
   * 下标：`sub`
   * ...
4. 水平线：`<hr>`
5. 注释：`<!--这是一个注释-->`
6. 链接：`<a href="https://www.baidu.com/">百度</a>`
   * target属性：(target="blank"打开新的页面，同时用rel使新页面没有控制权，让网站更加安全)
    ```html
    <a href="https://www.baidu.com" target="_blank" rel="noopener noreferrer">百度</a>
    ```
   * id属性：书签标记，不显示，可以查看
   * `style="text-decoration:none;`：没有下划线的链接
7. 头部：`<head>`  
   可以添加在头部区域的元素标签为: `<title>`, `<style>`, `<meta>`, `<link>`, `<script>`, `<noscript>` 和 `<base>`。
   * `<title>`：标题
   * `<base>`(空)：文档中所有的链接标签的默认链接（方便用相对地址插入图片，以及统一设置属性（target））
      ```html
      <base href="http://www.runoob.com/images/" target="_blank">
      ```
   * `<link>`（空）：定义文档与外部资源之间的关系。
      ```html
      <link rel="stylesheet" type="text/css" href="mystyle.css">
      ```
   * `<style>`：定义样式文件引用地址。
      ```html
      <style type="text/css">
         h1{color:red}
         body {background-color:yellow}
         p {color:blue}
      </style>
      ```
   * `<meta>`（空）：元数据。
     1. 为搜索引擎定义关键词`<meta name="author" content="HTML">`
     2. 每30秒钟刷新当前页面`<meta http-equiv="refresh" content="30">`
   * `<script>`：加载脚本文件。
8. 注意：html5的特征：`<!DOCTYPE html>`  
   * 省略`html`，`<head>`，`<body>`等元素。
   * 省略`<p>`结束标记。
   * 简化`<meta>`：`<meta charset="UTF-8">`
## 二、样式 -- CCS
1. 内联样式：直接在特定的标签里面加  
    ```html
   <h1 style="text-align:center;">居中对齐的标题</h1>
   <p style="font-family:arial;color:red;font-size:20px;">一个段落。</p>
   ```
2. 内部样式表
   ```html
   <head>
   <style type="text/css">
   body {background-color:yellow;text-align: center;}
   p {color:blue;text-align: center;}
   </style>
   </head>
   ```
3. 外部样式表
   ```html
   <head>
   <link rel="stylesheet" type="text/css" href="mystyle.css">
   </head>
   ```
4. 新版本不建议使用
   * 不建议使用的标签有: `<font>`, `<center>`, `<strike>`
   * 不建议使用的属性: color 和 bgcolor.
## 三、图形元素
1. 图像
   ```html
   <img src="/images/chrome.gif" alt="Google Chrome" width="33" height="32">
   ```
   1. 定义图像：`<img>` 空标签
      1. 源属性：src="url"
      2. alt属性：alt="替换文本"。无法载入图像时，替换文本属性告诉读者失去的信息。
   2. 定义图像地图：`map`。定义图像地图中可点击区域：`area`。(可点击图中不同的部分，转到不同的链接)
2. 表格：先定义行。`<tr>`是行，`<td>`是单元格，`<th>`是表头（居中加粗）。`<caption>`加标题。默认无边框，border="1"有边框。cellpadding是单元格间距。
   ```html
   <table border="1"，cellpadding="10">
      <tr>
        <th>Header 1</th>
        <th>Header 2</th>
      </tr>
      <tr>
         <td>row 1, cell 1</td>
         <td>row 1, cell 2</td>
      </tr>
      <tr>
         <td>row 2, cell 1</td>
         <td>row 2, cell 2</td>
      </tr>
   </table>
   ```
3. 列表
   1. 无序列表（UNordered List）
      ```html
      <ul>
      <li>项目</li>
      <li>项目</li>
      </ul>
      ```
   2. 有序列表（Ordered List）
      ```html
      <ol>
      <li>第一项</li>
      <li>第二项</li>
      </ol>
      ```
   3. 自定义列表：`<dt>`不缩进，`<dd>`缩进
      ```html
      <dl>
      <dt>Coffee</dt>
      <dd>- black hot drink</dd>
      </dl>
      ```
4. 区块（与CCS一起用，设定样式）
   1. `<div>`组合块级元素，通常会以新行来开始（和结束）：`<h1>`, `<p>`, `<ul>`, `<table>`
   2. `<span>`组合内联元素，通常不以新行开始：`<b>`, `<td>`, `<a>`, `<img>`
5. 表单：`<input type="..." name="..." value="...">`value是显示的
   1. 输入元素
      ```html
      <form>
      First name: <input type="text" name="firstname"><br>
      Last name: <input type="text" name="lastname"><br>
      Password: <input type="password" name="pwd">
      </form>
      ```
   2. 选择按钮：单选（圆）type="radio"。复选（方）type="checkbox"。按钮：button
      ```html
      <form>
      <input type="radio" name="sex" value="male">Male<br>
      <input type="radio" name="sex" value="female">Female
      </form>
      ```
   3. 提交按钮：`<input type="submit"> `
      ```html
      <form name="input" action="html_form_action.php" method="get">
      Username: <input type="text" name="user">
      <input type="submit" value="Submit">
      </form>
      ```
   4. 下拉列表：
      ```html
      <form action="">
         <select name="cars">
            <option value="volvo">Volvo</option>
            <option value="saab">Saab</option>
            <option value="fiat">Fiat</option>
            <option value="audi">Audi</option>
         </select>
      </form>
      ```
6. 框架`<iframe>`：在一个小框中显示另外一个网页
   1. 属性：height高度，width宽度，frameborder="0"移除边框
   2. 例子：
      ```html
      <iframe src="demo_iframe.htm" name="iframe_a"></iframe>
      <p><a href="//www.runoob.com" target="iframe_a">RUNOOB.COM</a></p>
      ```
      注：a标签的target是ifram_a（一个iframe名），所以点了链接后在这个iframe框架中显示网页。
## 四、颜色
1. RGB：三种颜色 红，绿，蓝的组合从0到255
   * RGBA：多一个Alpha通道，设置颜色透明度（0~1，0是全透明）
   `<p style="background-color:rgba(255,255,0,0.5)">通过 rbg 值设置背景颜色</p>`
2. 141个颜色名称：17标准 + 124
3. 颜色值（16进制，3位/6位）：#00F，#0000FF，rgb(0,0,255)
## 五、脚本 -- JavaScript
```html
<script>
document.write("Hello World!")
</script>
<noscript>抱歉，你的浏览器不支持 JavaScript!</noscript>
```
## 六、字符实体
HTML中的预留字符必须被替换为字符实体  
* 小于号：`&lt`; 或 `&#60;` 或 `&#060;`
* 不间断空格(Non-breaking Space)：`&nbsp;`
* 结合音标符：`a&#769;`
## 七、URL
语法规则：  
http://www.runoob.com/html/html-tutorial.html   
scheme://host.domain:port/path/filename
* scheme - 定义因特网服务的类型。最常见的类型是 http（https加密，ftp下载，file本机）。
* host - 定义域主机（http 的默认主机是 www）。
* domain - 定义因特网域名，比如 runoob.com
* :port - 定义主机上的端口号（http 的默认端口号是 80）
* path - 定义服务器上的路径（如果省略，则文档必须位于网站的根目录中）。
* filename - 定义文档/资源的名称
## 八、XHTML
XHTML 是以 XML 格式编写的 HTML。
1. 文档：
   1. XHTML DOCTYPE 是强制性的。
   2. `<html>` 中的 XML namespace 属性是强制性的,`<html>`、`<head>`、`<title>` 以及 `<body>` 也是强制性的
2. 元素：
   1. 元素必须小写，必须正确嵌套，必须始终关闭。空元素必须包含关闭标签（`<img src="happy.gif" alt="Happy face" />`，`<br />`）。
   2. 文档必须有一个根元素。`<html xmlns="http://www.w3.org/1999/xhtml"></html>`
3. 属性：属性必须小写，必须用双引号包围，属性简写是禁止的。