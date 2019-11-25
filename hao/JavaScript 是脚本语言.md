## JavaScript 是脚本语言

JavaScript 是一种轻量级的编程语言。

JavaScript 是可插入 HTML 页面的编程代码。

JavaScript 插入 HTML 页面后，可由所有的现代浏览器执行。

JavaScript 很容易学习。

# JavaScript 用法

------

HTML 中的脚本必须位于 <script> 与 </script> 标签之间。

脚本可被放置在 HTML 页面的 <body> 和 <head> 部分中。

## <script> 标签

如需在 HTML 页面中插入 JavaScript，请使用 <script> 标签。

<script> 和 </script> 会告诉 JavaScript 在何处开始和结束。

<script> 和 </script> 之间的代码行包含了 JavaScript:

  <script>
  alert("我的第一个 JavaScript"); 
  </script>  

## <body> 中的 JavaScript

在本例中，JavaScript 会在页面加载时向 HTML 的 <body> 写文本：


<!DOCTYPE html>
<html>
<body> 
    .
    .
<script> 
document.write("<h1>这是一个标题</h1>"); document.write("<p>这是一个段落</p>");
</script>
    .
    .
</body> </html> 

## JavaScript 函数和事件

上面例子中的 JavaScript 语句，会在页面加载时执行。

通常，我们需要在某个事件发生时执行代码，比如当用户点击按钮时。

如果我们把 JavaScript 代码放入函数中，就可以在事件发生时调用该函数。

您将在稍后的章节学到更多有关 JavaScript 函数和事件的知识。

## 在 <head> 或者 <body> 的JavaScript

您可以在 HTML 文档中放入不限数量的脚本。

脚本可位于 HTML 的 <body> 或 <head> 部分中，或者同时存在于两个部分中。

通常的做法是把函数放入 <head> 部分中，或者放在页面底部。这样就可以把它们安置到同一处位置，不会干扰页面的内容。

## <head> 中的 JavaScript 函数

在本例中，我们把一个 JavaScript 函数放置到 HTML 页面的 <head> 部分。

该函数会在点击按钮时被调用：

 

```
<!DOCTYPE html>
<html>
<head>
<script>
 function myFunction()
 {     
document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数"; }
</script>
</head>
<body> 
<h1>我的 Web 页面</h1>
<p id="demo">一个段落</p>
<button type="button" onclick="myFunction()">尝试一下</button> 
</body> 
</html>  
```

## 外部的 JavaScript

也可以把脚本保存到外部文件中。外部文件通常包含被多个网页使用的代码。

外部 JavaScript 文件的文件扩展名是 .js。

如需使用外部文件，请在 <script> 标签的 "src" 属性中设置该 .js 文件：

```
<!DOCTYPE html>
<html>
<body>
<script src="myScript.js"></script>
</body>
</html>
```

你可以将脚本放置于 <head> 或者 <body>中，放在 <script> 标签中的脚本与外部引用的脚本运行效果完全一致。

myScript.js 文件代码如下：

```
function myFunction()
{
    document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数";
}
```

# JavaScript 输出

JavaScript 没有任何打印或者输出的函数。

## JavaScript 显示数据

JavaScript 可以通过不同的方式来输出数据：

- 使用 **window.alert()** 弹出警告框。
- 使用 **document.write()** 方法将内容写到 HTML 文档中。
- 使用 **innerHTML** 写入到 HTML 元素。
- 使用 **console.log()** 写入到浏览器的控制台。

## 使用 window.alert()

你可以弹出警告框来显示数据：

```
<!DOCTYPE html>
<html>
<body>

<h1>我的第一个页面</h1>
<p>我的第一个段落。</p>

<script>
window.alert(5 + 6);
</script>

</body>
</html>
```

## 操作 HTML 元素

如需从 JavaScript 访问某个 HTML 元素，您可以使用 document.getElementById(*id*) 方法。

请使用 "id" 属性来标识 HTML 元素，并 innerHTML 来获取或插入元素内容：

```
<!DOCTYPE html>
<html>
<body>

<h1>我的第一个 Web 页面</h1>

<p id="demo">我的第一个段落</p>

<script>
document.getElementById("demo").innerHTML = "段落已修改。";
</script>

</body>
</html>
```

以上 JavaScript 语句（在 <script> 标签中）可以在 web 浏览器中执行：

**document.getElementById("demo")** 是使用 id 属性来查找 HTML 元素的 JavaScript 代码 。

**innerHTML = "段落已修改。"** 是用于修改元素的 HTML 内容(innerHTML)的 JavaScript 代码。

## 在本教程中

在大多数情况下，在本教程中，我们将使用上面描述的方法来输出：

上面的例子直接把 id="demo" 的 <p> 元素写到 HTML 文档输出中：

## 写到 HTML 文档

出于测试目的，您可以将JavaScript直接写在HTML 文档中：

```
<!DOCTYPE html>
<html>
<body>

<h1>我的第一个 Web 页面</h1>

<p>我的第一个段落。</p>

<script>
document.write(Date());
</script>

</body>
</html>
```

| <img src="https://www.runoob.com/images/lamp.jpg" alt="Note" style="zoom: 200%;" /> | 请使用 document.write() 仅仅向文档输出写内容。如果在文档已完成加载后执行 document.write，整个 HTML 页面将被覆盖。 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
|                                                              |                                                              |

```
<!DOCTYPE html>
<html>
<body>

<h1>我的第一个 Web 页面</h1>

<p>我的第一个段落。</p>

<button onclick="myFunction()">点我</button>

<script>
function myFunction() {
    document.write(Date());
}
</script>

</body>
</html>

```

## 写到控制台

如果您的浏览器支持调试，你可以使用 **console.log()** 方法在浏览器中显示 JavaScript 值。

浏览器中使用 F12 来启用调试模式， 在调试窗口中点击 "Console" 菜单。

```
<!DOCTYPE html>
<html>
<body>

<h1>我的第一个 Web 页面</h1>

<script>
a = 5;
b = 6;
c = a + b;
console.log(c);
</script>

</body>
</html>
```

 实例 console 截图： 

![](https://www.runoob.com/wp-content/uploads/2013/08/console-log.jpg) 

## 您知道吗?

| ![Note](https://www.runoob.com/images/lamp.jpg) | 程序中调试是测试，查找及减少bug(错误)的过程。 |
| ----------------------------------------------- | --------------------------------------------- |
|                                                 |                                               |

# JavaScript 语法

------

JavaScript 是一个程序语言。语法规则定义了语言结构。

------

## JavaScript 语法

JavaScript 是一个脚本语言。

它是一个轻量级，但功能强大的编程语言。

------

## JavaScript 字面量

在编程语言中，一般固定值称为字面量，如 3.14。

**数字（Number）字面量** 可以是整数或者是小数，或者是科学计数(e)。

```
3.14

1001

123e5
```

**字符串（String）字面量** 可以使用单引号或双引号:

```
"John Doe"

'John Doe'
```

 **表达式字面量** 用于计算： 

```
5 + 6

5 * 10
```

 **数组（Array）字面量** 定义一个数组： 

```
[40, 100, 1, 5, 25, 10]
```

**对象（Object）字面量** 定义一个对象：

```
{firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"}
```

**函数（Function）字面量** 定义一个函数：

```
function myFunction(a, b) { return a * b;}
```

## JavaScript 变量

在编程语言中，变量用于存储数据值。

JavaScript 使用关键字 **var** 来定义变量， 使用等号来为变量赋值：

```
var x, length

x = 5

length = 6
```

 变量可以通过变量名访问。在指令式语言中，变量通常是可变的。字面量是一个恒定的值。 

| ![Note](https://www.runoob.com/images/lamp.jpg) | 变量是一个**名称**。字面量是一个**值**。 |
| ----------------------------------------------- | ---------------------------------------- |
|                                                 |                                          |

## JavaScript 操作符

JavaScript使用 **算术运算符** 来计算值:

```
5 + 6) * 10
```

 JavaScript使用**赋值运算符**给变量赋值： 

```
x = 5
y = 6
z = (x + y) * 10
```

 JavaScript语言有多种类型的运算符 

| 类型                   | 实例      | 描述                   |
| :--------------------- | :-------- | :--------------------- |
| 赋值，算术和位运算符   | = + - * / | 在 JS 运算符中描述     |
| 条件，比较及逻辑运算符 | == != < > | 在 JS 比较运算符中描述 |

## JavaScript 语句

在 HTML 中，JavaScript 语句向浏览器发出的命令。

语句是用分号分隔：

```
x = 5 + 6;
y = x * 10;
```

## JavaScript 关键字

JavaScript 关键字用于标识要执行的操作。

和其他任何编程语言一样，JavaScript 保留了一些关键字为自己所用。

**var** 关键字告诉浏览器创建一个新的变量：

```
var x = 5 + 6;
var y = x * 10;
```

JavaScript 同样保留了一些关键字，这些关键字在当前的语言版本中并没有使用，但在以后 JavaScript 扩展中会用到。

以下是 JavaScript 中最重要的保留字（按字母顺序）：

| abstract | else       | instanceof | super        |
| -------- | ---------- | ---------- | ------------ |
|          |            |            |              |
| boolean  | enum       | int        | switch       |
|          |            |            |              |
| break    | export     | interface  | synchronized |
|          |            |            |              |
| byte     | extends    | let        | this         |
|          |            |            |              |
| case     | false      | long       | throw        |
|          |            |            |              |
| catch    | final      | native     | throws       |
|          |            |            |              |
| char     | finally    | new        | transient    |
|          |            |            |              |
| class    | float      | null       | true         |
|          |            |            |              |
| const    | for        | package    | try          |
|          |            |            |              |
| continue | function   | private    | typeof       |
|          |            |            |              |
| debugger | goto       | protected  | var          |
|          |            |            |              |
| default  | if         | public     | void         |
|          |            |            |              |
| delete   | implements | return     | volatile     |
|          |            |            |              |
| do       | import     | short      | while        |
|          |            |            |              |
| double   | in         | static     | with         |

## JavaScript 注释

下面的例子使用多行注释来解释代码：

不是所有的 JavaScript 语句都是"命令"。双斜杠 **//** 后的内容将会被浏览器忽略：

```
// 我不会执行
```

## JavaScript 多行注释

多行注释以 **/\*** 开始，以 ***/** 结尾。

## JavaScript 数据类型

JavaScript 有多种数据类型：数字，字符串，数组，对象等等：

```
var length = 16;                  // Number 通过数字字面量赋值
var points = x * 10;               // Number 通过表达式字面量赋值
var lastName = "Johnson";             // String 通过字符串字面量赋值
var cars = ["Saab", "Volvo", "BMW"];       // Array 通过数组字面量赋值
var person = {firstName:"John", lastName:"Doe"}; // Object 通过对象字面量赋值
```



------

## 数据类型的概念

编程语言中，数据类型是一个非常重要的内容。

为了可以操作变量，了解数据类型的概念非常重要。

如果没有使用数据类型，以下实例将无法执行：

16 + "Volvo"

16 加上 "Volvo" 是如何计算呢? 以上会产生一个错误还是输出以下结果呢？

"16Volvo"

你可以在浏览器尝试执行以上代码查看效果。

在接下来的章节中你将学到更多关于数据类型的知识。

------

## JavaScript 函数

JavaScript 语句可以写在函数内，函数可以重复引用：

**引用一个函数** = 调用函数(执行函数内的语句)。

```
function myFunction(a, b) {
  return a * b;                // 返回 a 乘以 b 的结果
}
```

------

## JavaScript 字母大小写

JavaScript 对大小写是敏感的。

当编写 JavaScript 语句时，请留意是否关闭大小写切换键。

函数 **getElementById** 与 **getElementbyID** 是不同的。

同样，变量 **myVariable** 与 **MyVariable** 也是不同的。

------

## JavaScript 字符集

JavaScript 使用 Unicode 字符集。

Unicode 覆盖了所有的字符，包含标点等字符。

如需进一步了解，请学习我们的 [完整 Unicode 参考手册](https://www.runoob.com/charsets/ref-html-utf8.html)。

------

## 您知道吗?

| ![Note](https://www.runoob.com/images/lamp.jpg) | JavaScript 中，常见的是驼峰法的命名规则，如 lastName (而不是lastname)。 |
| ----------------------------------------------- | ------------------------------------------------------------ |
|                                                 |                                                              |

## JavaScript 语句标识符

JavaScript 语句通常以一个 **语句标识符** 为开始，并执行该语句。

语句标识符是保留关键字不能作为变量名使用。

下表列出了 JavaScript 语句标识符 (关键字) ：

| 语句         | 描述                                                         |
| :----------- | :----------------------------------------------------------- |
| break        | 用于跳出循环。                                               |
| catch        | 语句块，在 try 语句块执行出错时执行 catch 语句块。           |
| continue     | 跳过循环中的一个迭代。                                       |
| do ... while | 执行一个语句块，在条件语句为 true 时继续执行该语句块。       |
| for          | 在条件语句为 true 时，可以将代码块执行指定的次数。           |
| for ... in   | 用于遍历数组或者对象的属性（对数组或者对象的属性进行循环操作）。 |
| function     | 定义一个函数                                                 |
| if ... else  | 用于基于不同的条件来执行不同的动作。                         |
| return       | 退出函数                                                     |
| switch       | 用于基于不同的条件来执行不同的动作。                         |
| throw        | 抛出（生成）错误 。                                          |
| try          | 实现错误处理，与 catch 一同使用。                            |
| var          | 声明一个变量。                                               |
| while        | 当条件语句为 true 时，执行语句块。                           |

# JavaScript 数据类型

------

**值类型(基本类型)**：字符串（String）、数字(Number)、布尔(Boolean)、对空（Null）、未定义（Undefined）、Symbol。

**引用数据类型**：对象(Object)、数组(Array)、函数(Function)。

> **注：**Symbol 是 ES6 引入了一种新的原始数据类型，表示独一无二的值。

## JavaScript 拥有动态类型

JavaScript 拥有动态类型。这意味着相同的变量可用作不同的类型：

## 实例

var x;        // x 为 undefined
var x = 5;      // 现在 x 为数字
var x = "John";   // 现在 x 为字符串



------

## JavaScript 字符串

字符串是存储字符（比如 "Bill Gates"）的变量。

字符串可以是引号中的任意文本。您可以使用单引号或双引号：

## 实例

var carname="Volvo XC60";
var carname='Volvo XC60';

您可以在字符串中使用引号，只要不匹配包围字符串的引号即可：

## 实例

var answer="It's alright";
var answer="He is called 'Johnny'";
var answer='He is called "Johnny"';


[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjs_datatypes_string)

您将在本教程的高级部分学到更多关于字符串的知识。

------

## JavaScript 数字

JavaScript 只有一种数字类型。数字可以带小数点，也可以不带：

## 实例

var x1=34.00;   //使用小数点来写
var x2=34;     //不使用小数点来写

极大或极小的数字可以通过科学（指数）计数法来书写：

## 实例

var y=123e5;   // 12300000
var z=123e-5;   // 0.00123


[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjs_numbers)

您将在本教程的高级部分学到更多关于数字的知识。

------

## JavaScript 布尔

布尔（逻辑）只能有两个值：true 或 false。

var x=true;
var y=false;

布尔常用在条件测试中。您将在本教程稍后的章节中学到更多关于条件测试的知识。

------

## JavaScript 数组

下面的代码创建名为 cars 的数组：

var cars=new Array();
cars[0]="Saab";
cars[1]="Volvo";
cars[2]="BMW";

或者 (condensed array):

var cars=new Array("Saab","Volvo","BMW");

或者 (literal array):

## 实例

var cars=["Saab","Volvo","BMW"];


[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjs_datatypes_array)

数组下标是基于零的，所以第一个项目是 [0]，第二个是 [1]，以此类推。

您将在本教程稍后的章节中学到更多关于数组的知识。

------

## JavaScript 对象

对象由花括号分隔。在括号内部，对象的属性以名称和值对的形式 (name : value) 来定义。属性由逗号分隔：

var person={firstname:"John", lastname:"Doe", id:5566};

上面例子中的对象 (person) 有三个属性：firstname、lastname 以及 id。

空格和折行无关紧要。声明可横跨多行：

var person={
firstname : "John",
lastname : "Doe",
id    : 5566
};

对象属性有两种寻址方式：

## 实例

name=person.lastname;
name=person["lastname"];


[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjs_datatypes_object)

您将在本教程稍后的章节中学到更多关于对象的知识。

------

## Undefined 和 Null

Undefined 这个值表示变量不含有值。

可以通过将变量的值设置为 null 来清空变量。

## 实例

cars=null;
person=null;


[尝试一下 »](https://www.runoob.com/try/try.php?filename=tryjs_undefined)



------

## 声明变量类型

当您声明新变量时，可以使用关键词 "new" 来声明其类型：

var carname=new String;
var x=   new Number;
var y=   new Boolean;
var cars=  new Array;
var person= new Object;



| ![lamp](https://www.runoob.com/images/lamp.jpg) | JavaScript 变量均为对象。当您声明一个变量时，就创建了一个新的对象。 |
| ----------------------------------------------- | ------------------------------------------------------------ |
|                                                 |                                                              |

# JavaScript 对象

------

JavaScript 对象是拥有属性和方法的数据。

------

## 真实生活中的对象，属性和方法

真实生活中，一辆汽车是一个对象。

对象有它的属性，如重量和颜色等，方法有启动停止等:

| 对象                                                      | 属性                                                         | 方法                                              |
| :-------------------------------------------------------- | :----------------------------------------------------------- | :------------------------------------------------ |
| ![img](https://www.runoob.com/images/objectExplained.gif) | car.name = Fiat  car.model = 500  car.weight = 850kg  car.color = white | car.start()  car.drive()  car.brake()  car.stop() |

所有汽车都有这些属性，但是每款车的属性都不尽相同。

所有汽车都拥有这些方法，但是它们被执行的时间都不尽相同。

## JavaScript 对象

在 JavaScript中，几乎所有的事物都是对象。

# JavaScript 函数

------

函数是由事件驱动的或者当它被调用时执行的可重复使用的代码块。

## 实例

```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>测试实例</title>
<script>
function myFunction()
{
    alert("Hello World!");
}
</script>
</head>
 
<body>
<button onclick="myFunction()">点我</button>
</body>
</html>
```

## JavaScript 函数语法

函数就是包裹在花括号中的代码块，前面使用了关键词 function：

```
function functionname()
{
    // 执行代码
}
```

