# CCS
```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
<style>
#para1
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
<p id="para1">这个段落采用CSS样式化。</p>
</body>
</html>
```
## 选择器
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
2. class选择器(CS)：.前面也可以加某种元素（比如p.value），用来限制只有一种元素能用
    ```html
    <style>
    .value{
      text-align:center;
    }
    </style>
    <!--下面的文字是居中对齐的-->
    <p class="value">center text</p>
    ```
3. 还有元素选择器(ES)和属性选择器(AS)