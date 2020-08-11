# JavaScript初级教程
## 一、基本知识
1. 基本用法
   1. 在网页上面写脚本：`<script></script>`
   2. 位置：`<head>`，`<body>`或外部.js文件`<script src="myScript.js"></script>`
2. 输出
   1. 弹出警告框：`window.alert()`
   2. 修改HTML元素：`document.getElementById("demo").innerHTML = "修改后的段落";`
   3. 写到HTML文档：`document.write();`
      * 如果在文档已完成加载后（如按钮）执行 document.write，整个 HTML 页面将被覆盖。
   4. 写到控制台：console.log()
3. 语法
   1. 字面量（固定常量）：数字，字符串，对象，函数
      1. 字符串用''或""都行，字符串中用\添加特殊字符（转义字符）
      2. 数组用[]
      3. 对象{firstName:"John", lastName:"Doe", age:50}
      4. 函数function myFunction(a,b){return a*b;}
   2. 变量，var定义。=赋值。驼峰法命名。一个var能定义多个。
   3. 注释//，/**/
4. 数据类型
   1. JavaScript拥有动态类型，相同的变量可用作不同的类型（数字能改成字符串）。
   2. 数组：`var cars = new Array();`或`var arr = ['a', 'b', 'c' ];`
5. 对象：
   1. 定义
      ```JavaScript
      var person={
         firstname:"John", 
         lastname:"Doe", 
         id:5566
         fullName : function() 
	      {
         return this.firstName + " " + this.lastName;
         }
      };
      ```
   1. 访问对象属性
      * `name=person.lastname;`
      * `name=person["lastname"];`
   2. 访问对象方法
      * `name = person.fullName();`返回返回值
      * `name = person.fullName;`返回函数的定义（字符串）,作文一个属性。
   3. 把值赋给尚未声明的变量，该变量将被自动作为 window 的一个属性。`var2 = 2;`访问`window.var2;`删除`delete var2;` 
6. 函数
   1. `function myFunction(name,job){alert("Welcome " + name + ", the " + job);return...}`
   2. 函数内部的变量是局部变量，函数内部可见，函数运行完毕就删除。全局变量在所有脚本和函数均可使用，页面关闭后删除。
7. HTML事件：事件触发时 JavaScript 可以执行一些代码（点击某个元素onclick，完成页面加载onload）
8. 字符串：不要创建String对象。它会拖慢执行速度，并可能产生其他副作用。
9. 运算符：与java，C语言基本一致。
   1. 字符串可以加，连接用
   2. 字符串+数字，返回字符串
   3. 比较运算符：!==不绝对等于：值和类型至少有一个不相等。===全等，值和类型都必须相等。
   4. 逻辑运算符：&&，||，!
   5. 条件运算符：variablename=(condition)?value1:value2 
10. 条件语句：
    1. if else
    2. switch(n){case 1:...break;default:}
11. 循环语句：
    1. for/in循环：循环遍历对象的属性
      ```JavaScript
      var person={fname:"John",lname:"Doe",age:25}; 
      for (x in person)  // x 为属性名
      {
         txt=txt + person[x];
      }
      ```
    2. length属性可获得数组的长度
    3. break跳出循环，continue开始下一次循环
    4. 标签：标记一个代码块。`labelname:{...}`，用`break/continue labelname`能跳出代码块
12. 类型转换
    1. typeof查看变量的数据类型。`arr instanceof Array`看arr是不是Array类型的对象。
        1. 数组/对象是object
        2. null是类型是object，用来清空对象。
        3. undefined的类型是undefined，用来清空任何变量。
    2. 数据类型：string，number(NaN是number)，boolean，object，function，symbol
    3. 对象类型：Object，Date，Array(但是Date和Array的typeof都是返回object)
    4. 类型转换：
       1. 全局方法String(),Number(),Boolean()
       2. xx.toString()，xx.getTime()
       3. var x = + y; 把字符串y变成数字。

# JavaScript高级教程
