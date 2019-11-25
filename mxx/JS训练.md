## JS训练

#### 一    .安装Sublime编辑器

#### 二   .JS基础

##### 1.简介

```
JS 是一种网页编程技术 , 用于向网页添加交互行为的编程技术 . 
JS 是一种基于对象 和 事件驱动的 解释性脚本语言 ,由浏览器直接解析执行代码 , 不进行预编译.

特点:
    1.  JS代码可以直接嵌入到HTML文件中
    2.  可以使用任何的文本编辑器编写代码 
    3.  基于对象 内置了大量的可用对象.
    4.  与Java不同, 代码不进行预编译, 直接解析执行.

缺点:
    不具备计算机本地资源的操作能力. 

作用:
    1.  客户端的逻辑运算    
    2.  网页事件处理
    3.  表单的合法性验证
    4.  动画效果制作

    可以减轻服务器的压力.
```

##### 2. 定义JS代码的三种方式 （*********）

```
1.  定义在元素的事件属性中
        <button onclick="alert('从前有座山')">按钮</button>

2.  定义在网页的script标签中
        <script type="text/javascript">
            for(i=0;i<100;i++){
                alert("嘿嘿嘿"+i);
            }
        </script>
3.  定义在外部的.js文件中.
        <script type="text/javascript" src="js/demo1.js"></script>
```

##### 3. JS的三种弹出窗

```
任何的JS弹出窗 , 都会导致浏览器的线程阻塞! 程序等待用户点击关闭 再向下执行.

1.  提示窗口
        alert("弹出的内容");

2.  弹出信息问询框 , 具备确定和取消按钮, 点击确定时 返回true ,点击取消或关闭时返回false
        confirm("弹出的内容");

3.  弹出输入框 , 具备确定和取消按钮 ,点击确定返回输入内容, 点击取消或关闭 返回null
        prompt("提示输入的内容");
```

##### 4. JS 事件列表 

```
属性 值 描述 4 5 
onabort script  发生 abort 事件时运行脚本。   5 
onbeforeonload script  在元素加载前运行脚本。   5 
onblur script  当元素失去焦点时运行脚本。 4 5 
onchange script 当元素改变时运行脚本。 4 5 
onclick script  在鼠标点击时允许脚本。 4 5 
oncontextmenu script  当菜单被触发时运行脚本。   5 
ondblclick script  当鼠标双击时运行脚本。 4 5 
ondrag script  只要脚本在被拖动就允许脚本。   5 
ondragend script  在拖动操作结束时运行脚本。   5 
ondragenter script  当元素被拖动到一个合法的放置目标时，执行脚本。   5 
ondragleave script  当元素离开合法的放置目标时。   5 
ondragover script  只要元素正在合法的放置目标上拖动时，就执行脚本。   5 
ondragstart script  在拖动操作开始时执行脚本。   5 
ondrop script  当元素正在被拖动时执行脚本。   5 
onerror script  当元素加载的过程中出现错误时执行脚本。   5 
onfocus script  当元素获得焦点时执行脚本。 4 5 
onkeydown script  当按钮按下时执行脚本。 4 5 
onkeypress script  当按键被按下时执行脚本。 4 5 
onkeyup script  当按钮松开时执行脚本。 4 5 
onload script 当文档加载时执行脚本。 4 5 
onmessage script  当 message 事件触发时执行脚本。   5 
onmousedown script  当鼠标按钮按下时执行脚本。 4 5 
onmousemove script  当鼠标指针移动时执行脚本。 4 5 
onmouseover script 当鼠标指针移动到一个元素上时执行脚本。 4 5 
onmouseout script 当鼠标指针移出元素时执行脚本。 4 5 
onmouseup script  当鼠标按钮松开时执行脚本。 4 5 
onmousewheel script  当鼠标滚轮滚动时执行脚本。   5 
onreset script  当表单重置时执行脚本。不支持。 4   
onresize script  当元素调整大小时运行脚本。   5 
onscroll script  当元素滚动条被滚动时执行脚本。   5 
onselect script  当元素被选中时执行脚本。 4 5 
onsubmit script 当表单提交时运行脚本。 4 5 
onunload script 当文档卸载时运行脚本。   5 
```

##### 5. 定义变量 

```
Java    :   一门强类型的语言;
JS      :   一门弱类型的语言;

语法格式:   var 变量名 = 初始化值;
```

##### 6. 数据类型 

```
-   基本数据类型
        -   number  :   数值型.
        -   boolean :   布尔类型
        -   string  :   字符串类型

-   复杂数据类型
        -   Array   :   数组
        -   Object  :   对象

-   特殊数据类型
        -   null    :   空
        -   undefined:  未定义  , 未定义的数据 判断是否等于null时, 结果为true
```

##### 7.switch语法

```
switch(n) {  
        case 1:        执行代码块 1        break;   
        case 2:        执行代码块 2        break;    
        default:        与 case 1 和 case 2 不同时执行的代码 
}
//工作原理：首先设置表达式 n（通常是一个变量）。随后表达式的值会与结构中的每个 case 的值做比较。如果存在匹配，则与该 case 关联的代码块会被执行。请使用 break 来阻止代码自动地向下一个 case 运行。
```

##### 8 .HTML语法格式 

```
HTML文档通常存储在.html 文件中 或 htm文件中.

基础网页模板:

    由三部分组成.
        1.  HTML文档声明
            <!DOCTYPE html>
            <html>
        2.  网页标签 - 头部 : 用于描述网页
                <head>
                    <title>我们的第一个网页</title>
                </head>
        3.  网页标签 - 主体 : 网页显示的内容
                <body>Hello HTML</body>
            </html>
```

##### 9.head 中的常用子标签

```
-   title   :   网页的标题 , 在浏览器的标签位置显示..
-   meta    :   描述网页的编码, 移动设备优先 , 也常用于通知搜索引擎蜘蛛 搜索关键字.
-   style   :   用于描述样式表 , style标签中的语法格式 按照CSS格式编写.
-   script  :   用于描述脚本 , script标签中的语法格式, 按照JavaScript语法编写.
-   link    :   用于引入外部的样式表.
```

##### 10表单中常用的子标签  input 标签 

```
输入组件 , 用于接收用户的输入.
在表单提交时, 输入组件的内容 会以键值对的方式 发送给服务器.

属性:
    -   name    :   输入组件的名称, 在数据提交时,是键值对的 键.
    -   value   :   输入组件的内容, 在数据提交时,是键值对的 值. 当输入组件的形态为输入框时, value也是输入框中的内容
    -   placeholder : 当输入组件的形态为输入框,  用于提示用户输入.
    -   checked :   输入组件为单选/复选框时 , 默认选中. HTML5boolean属性. 属性存在即为true

输入框的形态:
    type属性: 属性值是输入框的各种形态:
        -   text    :   默认值 , 文本输入框.
        -   password:   密码输入框
        -   number  :   数字输入框.
        -   color   :   颜色调色板
        -   radio   :   单选框 , 一组单选框只能选中一个. 通过相同的name属性来分组.
        -   checkbox:   复选框
        -   file    :   文件上传选择框

        日期类型的输入组件形态:
            -   date    :   年月日选择框
            -   month   :   年月选择框
            -   week    :   年周选择框
            -   time    :   时间选择框
            -   datetime:   年月日时分选择框 (大多浏览器已经不支持了.)
            -   datetime-local  :   本地时区的  年月日时分选择框.

        按钮类型的输入组件形态:
            -   button  :   普通按钮 *
            -   reset   :   重置按钮, 点击后会导致表单所有内容重置.
            -   submit  :   提交按钮 *
            -   image   :   作用与submit一致, 不过此按钮不展示文字, 而是通过src属性展示图片.

        隐藏的输入组件:
            -   hidden  :   隐藏的输入框, 用于隐式的收集用户的信息.
```

##### 11. 数组 Array

```
格式:
    创建数组的格式:
        -   var 数组名 = new Array();
        -   var 数组名 = new Array(长度);
        -   var 数组名 = new Array(元素1,元素2,元素3,...元素n);
        -   var 数组名 = [元素1,元素2,元素3,...元素n];

注意: 
    Java中数组长度一经确定  无法改变.
    JS中数组的长度是可以任意扩容的.  数组的每一个下标, 更像是一个变量名. 可以任意赋值.  未赋值的下标默认值: undefined
```

##### 12. 正则表达式对象

```
使用步骤
    1.  创建正则对象
            var 对象名 = /正则表达式/g;
    2.  使用
            正则对象.test(要验证的数据)   :   返回boolean类型的值, 符合true , 不符合false
```

##### 13. 函数  (*********) 

```
定义函数的格式:

    function 函数名(形式参数列表){
        //函数体
    }

案例:
    定义一个函数, 拥有两个参数, 用于计算两个参数的和 , 并将计算结果返回

    function sum(x,y){
        return x+y;
    }

练习:    三目运算符
    定义一个函数, 函数中拥有四个参数 , 比较四个参数的大小, 将最大的参数值 返回.
    function max(q,w,e,r){
        return ((q>w?q:w)>e?(q>w?q:w):e)>r?((q>w?q:w)>e?(q>w?q:w):e):r;
    }
```

##### 14. 函数扩展 

```
函数也是一种变量 , 函数名 也是 变量名,  一个函数 也可以称其为 一个function类型的变量.

按照定义变量的方式, 来定义函数:

    var 函数名 = function(){

    }


按照new的方式 来定义函数:
    var 函数名 = new Function(可变长度的参数列表);
    参数列表:
        string类型的可变参数 , 参数列表的长度为0-n;
        第0-(n-1)的参数, 表示函数的形式参数列表.
        第n个参数表示函数体.

    例如:
        var sum = new Function("x","y","return x+y;");

    相当于:
        function sum(x,y){
            return x+y;
        }
```

##### 15. 全局函数

```
-   isNaN(变量)
        如果变量值为数字 , 则返回false !  
        如果变量值不是数字, 则返回true.

-   eval(字符串);
        将字符串 作为代码 解析执行.
```

##### 16. HTML DOM对象

```
HTML Document Object Model ( HTML文档对象模型 )
```

##### 17. 通过文档对象 document , 获取元素对象 (*********)

```
1.  通过元素的id属性值, 查找一个元素对象
        var 元素对象 = document.getElementById("id值");
2.  通过元素的名称 , 查找一个元素对象数组
        var 元素对象数组 = document.getElementsByTagName("标签名称");
3.  通过元素的class属性值, 查找一个元素对象数组
        var 元素对象数组 = document.getElementsByClassName("class值");
4.  通过元素的name属性值, 查找一个元素对象数组
        var 元素对象数组 = document.getElementsByName("name值");
```

##### 18. 如何操作元素的属性 (***)

```
设置属性值:
    元素对象.属性名 = 值;
获取属性值:
    var 属性值 = 元素对象.属性名;
```

```
例如:
    元素如下:
        <img id="img1" src="images/1.jpg" width="200px" height="200px">
    JS代码如下:
        var img1 = document.getElementById("img1");
        上述查找到的img1对象, 包含了img标签所有的属性, 但是只有src 和 width 以及 height 是有值的.

    操作属性代码如下:
        将图片的透明度设置为0.5:
            img1.style = "opacity:0.5";
        修改图片显示为images/2.jpg:
            img1.src = "images/2.jpg";


例如: 
    在用户输入完毕(输入框失去焦点)时 , 获取如下输入框的内容:
    <input id="input1" onblur="x1()">
    <script>
        function x1(){
            var input1 = document.getElementById("input1");
            var val = input1.value;
            alert("输入的内容:"+val);
        }
    </script>
```

##### 19. 特殊属性:

```
1.  class属性 :   class在JS中是关键字. 因为属性名的命名规则不允许使用关键字, 所以class的属性操作, 需要通过className属性来完成.

2.  标签内容        :   通过innerHTML属性 来操作开始标签 与 结束标签之间的部分.
```

##### 20. JS中定义对象的三种方式

```
JS中创建对象,  不需要提前编写类.
JS中可以先创建一个空对象 (不包含任何的属性和函数)
后续, 再给空对象 , 设置属性和函数.
```

###### 20-1. 格式1

```
    var 对象名 = new Object();

JS中给对象设置属性值,  如果对象中不存在此属性, 则创建属性并赋值.

案例:
    var person = new Object();
    person.name = "小泽马";
    person.age = 18;
    person.sex = "妖";
    person.length = "180mm";
    person.say = function(){
        alert("我是:"+this.name+" , 我今年"+this.age+"岁了 , 我的性别是: "+this.sex+" , 我的身长是:"+this.length);
    };

    person.say();
```

###### 20-2. 格式2

```
先创建对象模板, 然后通过new的方式, 来完成对象的创建.

格式:
    创建模板的格式:
        function 模板名称(形式参数列表){
            通过this , 给属性赋值.
        }
    使用模板的格式:
        var 对象名 = new 模板名称(实际参数列表);

案例:
    function Book(id,name,info){
        this.id = id;
        this.name = name;
        this.info = info;
        this.toString = function(){
            console.log("图书编号:"+this.id+" , 图书名称:"+this.name+" , 图书详情:"+this.info);
        };
    }

    var b = new Book(1,"小泽马老师 - 平沙落雁式","php高级导师 小泽马, 亲自配图编写武术秘籍 , 学习此秘籍, 可让家庭更和谐, 社会更安定");
    b.toString();
```

###### 20-3. 格式3 , 通过JSON来创建对象(*********)

```
JSON:   JavaScript Object Notation  JS对象简谱 , 是一种轻量级的数据交换格式.

格式:
    JSON中包含两大格式: JSON对象 和 JSON数组. 这两种格式可以互相嵌套.
        1.  JSON对象
                一个对象, 由一个大括号表示.
                括号中 描述对象的属性与函数 .  通过键值对来描述对象的属性与函数
                (可以理解为, 大括号中, 包含的是一个个的键值对.)
                格式:
                    键与值之间使用冒号连接, 多个键值对之间使用逗号分隔.
                    键值对的键 应使用引号引住 (通常Java解析时, 键不适用引号会报错. 而JS能正确解析.)
                    键值对的值, 可以是JS中的任意类型的数据

                例如: 描述一个人:
                //var person = {} 相当于  var person = new Object();
                var person = {
                    "name":"小泽马",
                    "age":18,
                    "say":function(){
                        alert("姓名:"+this.name+" , 年龄: "+this.age);
                    }
                };
                person.say();
        2.  JSON数组
            就是JS中的数组.

    案例:

        描述小泽马:
            var p = {
                "name":"小泽马",
                "age":18,
                "paoyou":["武藤老师","苍老师","天海老师","泷泽老师",{
                            "name":"加藤老师",
                            "info":"自带特技一阳指"
                        }],
                "haha":{
                    "name":"大长刀",
                    "length":"40m"
                }
            };
            alert(p.paoyou[4].info);
```

##### 21. JavaScript 显示数据

​	JavaScript 可以通过不同的方式来输出数据：

​			使用 **window.alert()** 弹出警告框。

​			使用  **document.write()** 方法将内容写到 HTML 文档中。

​			使用 **innerHTML** 写入到 HTML 元素。

​			使用 **console.log()** 写入到浏览器的控制台。

##### 22. JS常见面试题: 

```
Jquery中 , html函数 以 text函数, 在获取元素内容上, 有什么区别?

答:
    html函数与text函数, 都用于获取元素的内容.
    区别是:
        html函数 在获取内容时,  会得到html标签部分
        text函数 在获取内容时, 会忽略html标签部分

    例如: 获取如下div
        <div>从前有<span>座</span>山</div>
        html函数: 从前有<span>座</span>山
        text函数: 从前有座山 
```

#### 三：示例代码

##### 1. 定位指定文本首次出现的位置(indexOf)

```
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
</head>
<body>

<p id="demo">单击按钮来定位指定文本首次出现的位置。</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var str="Hello world, welcome to the universe.";
	var n=str.indexOf("welcome");
	document.getElementById("demo").innerHTML=n;
}
</script>

</body>
</html>
```

##### 2. substring() 方法用于提取字符串中介于两个指定下标之间的字符。

```
stringObject.substring(start,stop)

<script type="text/javascript">

var str="Hello world!"
document.write(str.substring(3))

</script>

//输出：lo world!
```

##### 3. 获取时间的方法解析：

```
	var myDate = new Date();
	var Y = myDate.getFullYear();    //获取完整的年份(4位,1970-????)
	var M = myDate.getMonth()+1;       //获取当前月份(0-11,0代表1月)
	var D = myDate.getDate();        //获取当前日(1-31)
	var h = myDate.getHours();       //获取当前小时数(0-23)
	var m = myDate.getMinutes();     //获取当前分钟数(0-59)
	var s = myDate.getSeconds();     //获取当前秒数(0-59)
```









































































































































