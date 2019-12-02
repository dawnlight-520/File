# 007  JavaScript 训练

### JavaScript 简介

JavaScript 是互联网上最流行的脚本语言，这门语言可用于 HTML 和 web，更可广泛用于服务器、PC、笔记本电脑、平板电脑和智能手机等设备。

JavaScript 是脚本语言

JavaScript 是一种轻量级的编程语言。

JavaScript 是可插入 HTML 页面的编程代码。

JavaScript 插入 HTML 页面后，可由所有的现代浏览器执行。

* JavaScript：直接写入 HTML 输出流

  ```
  document.write("<h1>这是一个标题</h1>");
  document.write("<p>这是一个段落。</p>");
  ```

* JavaScript：对事件的反应

  ```
  <button type="button" onclick="alert('欢迎!')">点我!</button>
  ```

* JavaScript：改变 HTML 内容

  ```
  x=document.getElementById("demo");  //查找元素
  x.innerHTML="Hello JavaScript";    //改变内容
  ```

* JavaScript：改变 HTML 样式

  ```
  x=document.getElementById("demo")  //找到元素 
  x.style.color="#ff0000";           //改变样式
  ```

* JavaScript：验证输入

  ```
  if isNaN(x) {
      alert("不是数字");
  }
  ```

### JavaScript 用法

HTML 中的脚本必须位于 <script> 与 </script> 标签之间。

脚本可被放置在 HTML 页面的 <body> 和 <head> 部分中。

* #### \<script> 标签

  如需在 HTML 页面中插入 JavaScript，请使用 <script> 标签。

<script> 和 </script> 会告诉 JavaScript 在何处开始和结束。

<script> 和 </script> 之间的代码行包含了 JavaScript:

```
<script type="text/javascript">
alert("我的第一个 JavaScript");
</script>
```

* ##### \<body> 中的 JavaScript

  ```
  <!DOCTYPE html>
  <html>
  <body>
  .
  .
  <script>
  document.write("<h1>这是一个标题</h1>");
  document.write("<p>这是一个段落</p>");
  </script>
  .
  .
  </body>
  </html>
  ```

* 在 <head> 或者 <body> 的JavaScript

  您可以在 HTML 文档中放入不限数量的脚本。

  脚本可位于 HTML 的 <body> 或 <head> 部分中，或者同时存在于两个部分中。

  通常的做法是把函数放入 <head> 部分中，或者放在页面底部。这样就可以把它们安置到同一处位置，不会干扰页面的内容。

* #### \<head> 中的 JavaScript 函数 

  把一个 JavaScript 函数放置到 HTML 页面的 <head> 部分,该函数会在点击按钮时被调用：

  ```
  <!DOCTYPE html>
  <html>
  <head>
  <script>
  function myFunction()
  {
      document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数";
  }
  </script>
  </head>
  <body>
  <h1>我的 Web 页面</h1>
  <p id="demo">一个段落</p>
  <button type="button" onclick="myFunction()">尝试一下</button>
  </body>
  </html>
  ```

* #### \<body> 中的 JavaScript 函数

  ```
  <!DOCTYPE html>
  <html>
  <body>
  <h1>我的 Web 页面</h1>
  <p id="demo">一个段落</p>
  <button type="button" onclick="myFunction()">尝试一下</button>
  <script>
  function myFunction()
  {
      document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数";
  }
  </script>
  </body>
  </html>
  ```

* #### 外部的 JavaScript

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

  将脚本放置于 <head> 或者 <body>中，放在 <script> 标签中的脚本与外部引用的脚本运行效果完全一致。

  myScript.js 文件代码如下：

  ```
  function myFunction()
  {
      document.getElementById("demo").innerHTML="我的第一个 JavaScript 函数";
  }
  注意外部脚本不能包含 <script> 标签。
  ```

  1、在标签中填写 onclick 事件调用函数时，不是 **onclick=函数名**， 而是 **onclick=函数名+()**，代码如下：

  ```
  <script> 
      function myfunction(){
           document.getElementById("demo").innerHTML="onclick事件触发";
          }</script>
      </head>
  <body>
      <h1 id="demo">一个段落</h1>
      <button onclick="myfunction()" type="button">点击这里</button>
  </body>
  ```

  2、外部 javascript 文件不使用 **** 标签，直接写 javascript 代码。

  3、HTML 输出流中使用 document.write，相当于添加在原有html代码中添加一串html代码。而如果在文档加载后使用（如使用函数），会覆盖整个文档。

  使用函数来执行document.write代码如下：

  ```
  <script>
  function myfunction(){
      document.write("使用函数来执行doucment.write，即在文档加载后再执行这个操作，会实现文档覆盖");
  }
  document.write("<h1>这是一个标题</h1>");
  document.write("<p>这是一个段落。</p>");
  </script>
  <p >
  您只能在 HTML 输出流中使用 <strong>document.write</strong>。
  如果您在文档已加载后使用它（比如在函数中），会覆盖整个文档。
  </p>
  <button type="button" onclick="myfunction()">点击这里</button>
  ```

  ### JavaScript Date（日期） 对象

  使用 getFullYear() 获取年份。

  getTime() 返回从 1970 年 1 月 1 日至今的毫秒数。

* #### 创建日期

  Date 对象用于处理日期和时间。

  可以通过 new 关键词来定义 Date 对象。以下代码定义了名为 myDate 的 Date 对象：

  有四种方式初始化日期:

  ```
  new Date() // 当前日期和时间
  new Date(milliseconds) //返回从 1970 年 1 月 1 日至今的毫秒数
  new Date(dateString)
  new Date(year, month, day, hours, minutes, seconds, milliseconds)
  ```

  上面的参数大多数都是可选的，在不指定的情况下，默认参数是0。

  实例化一个日期的一些例子：

  ```
  var today = new Date()
  var d1 = new Date("October 13, 1975 11:13:00")
  var d2 = new Date(79,5,24)
  var d3 = new Date(79,5,24,11,33,0)
  ```

* #### 设置日期

  通过使用针对日期对象的方法，我们可以很容易地对日期进行操作。

  在下面的例子中，我们为日期对象设置了一个特定的日期 (2010 年 1 月 14 日)：

  ```
  var myDate=new Date();
  myDate.setFullYear(2010,0,14);
  ```

  在下面的例子中，我们将日期对象设置为 5 天后的日期：

  ```
  var myDate=new Date();
  myDate.setDate(myDate.getDate()+5);
  ```

  **注意:** 如果增加天数会改变月份或者年份，那么日期对象会自动完成这种转换。

* #### 两个日期比较

  ```
  var x=new Date();
  x.setFullYear(2100,0,14);
  var today = new Date();
  
  if (x>today)
  {
      alert("今天是2100年1月14日之前");
  }
  else
  {
      alert("今天是2100年1月14日之后");
  }
  ```

* #### **把日期格式化为指定格式实例：**

  ```
  Date.prototype.format = function(fmt){
    var o = {
      "M+" : this.getMonth()+1,                 //月份
      "d+" : this.getDate(),                    //日
      "h+" : this.getHours(),                   //小时
      "m+" : this.getMinutes(),                 //分
      "s+" : this.getSeconds(),                 //秒
      "q+" : Math.floor((this.getMonth()+3)/3), //季度
      "S"  : this.getMilliseconds()             //毫秒
    };
  
    if(/(y+)/.test(fmt)){
      fmt=fmt.replace(RegExp.$1, (this.getFullYear()+"").substr(4 - RegExp.$1.length));
    }
          
    for(var k in o){
      if(new RegExp("("+ k +")").test(fmt)){
        fmt = fmt.replace(
          RegExp.$1, (RegExp.$1.length==1) ? (o[k]) : (("00"+ o[k]).substr((""+ o[k]).length)));  
      }       
    }
  
    return fmt;
  }
  
  document.getElementById("demo1").innerHTML=new Date(79,5,24,11,33,0).format("MM月dd日"); 
  
  var now = new Date();
  var nowStr = now.format("yyyy-MM-dd hh:mm:ss");
  document.getElementById("demo2").innerHTML=new Date().format("yyyy年MM月dd日");
  var nowStr = now.format("yyyy-MM-dd hh:mm:ss");
  document.getElementById("demo3").innerHTML=new Date().format("yyyy年MM月dd日hh小时mm分ss秒");
  ```

* #### 其他格式实例：

  ```
  alert(new Date().format("yyyy年MM月dd日"));
  alert(new Date().format("MM/dd/yyyy"));
  alert(new Date().format("yyyyMMdd"));
  alert(new Date().format("yyyy-MM-dd hh:mm:ss"));
  ```

  ### JavaScript 字符串

* #### 字符串长度

  可以使用内置属性 **length** 来计算字符串的长度：

  ```
  var txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
  var sln = txt.length;
  ```

* #### 特殊字符

  反斜杠是一个**转义字符**。 转义字符将特殊字符转换为字符串字符：

  转义字符 (\\) 可以用于转义撇号，换行，引号，等其他特殊字符。

  下表中列举了在字符串中可以使用转义字符转义的特殊字符：

  | \\'  | 单引号      |
  | ---- | ----------- |
  | \\"  | 双引号      |
  | \\\  | 反斜杠      |
  | \n   | 换行        |
  | \r   | 回车        |
  | \t   | tab(制表符) |
  | \b   | 退格符      |
  | \f   | 换页符      |

* #### 字符串方法

  | charAt()            | 返回指定索引位置的字符                                       |
  | ------------------- | ------------------------------------------------------------ |
  | charCodeAt()        | 返回指定索引位置字符的 Unicode 值                            |
  | concat()            | 连接两个或多个字符串，返回连接后的字符串                     |
  | fromCharCode()      | 将 Unicode 转换为字符串                                      |
  | indexOf()           | 返回字符串中检索指定字符第一次出现的位置                     |
  | lastIndexOf()       | 返回字符串中检索指定字符最后一次出现的位置                   |
  | localeCompare()     | 用本地特定的顺序来比较两个字符串                             |
  | match()             | 找到一个或多个正则表达式的匹配                               |
  | replace()           | 替换与正则表达式匹配的子串                                   |
  | search()            | 检索与正则表达式相匹配的值                                   |
  | slice()             | 提取字符串的片断，并在新的字符串中返回被提取的部分           |
  | split()             | 把字符串分割为子字符串数组                                   |
  | substr()            | 从起始索引号提取字符串中指定数目的字符                       |
  | substring()         | 提取字符串中两个指定的索引号之间的字符                       |
  | toLocaleLowerCase() | 根据主机的语言环境把字符串转换为小写，只有几种语言（如土耳其语）具有地方特有的大小写映射 |
  | toLocaleUpperCase() | 根据主机的语言环境把字符串转换为大写，只有几种语言（如土耳其语）具有地方特有的大小写映射 |
  | toLowerCase()       | 把字符串转换为小写                                           |
  | toString()          | 返回字符串对象值                                             |
  | toUpperCase()       | 把字符串转换为大写                                           |
  | trim()              | 移除字符串首尾空白                                           |
  | valueOf()           | 返回某个字符串对象的原始值                                   |

  ### JavaScript 正则表达式

* #### 含义

  正则表达式是由一个字符序列形成的搜索模式。

  正则表达式可用于所有文本搜索和文本替换的操作。

* #### 语法

  ```
  /正则表达式主体/修饰符(可选)
  ```

  其中修饰符是可选的。

  ```
  var patt = /runoob/i
  ```

  实例解析：

  **/runoob/i** 是一个正则表达式。

  **runoob** 是一个**正则表达式主体** (用于检索)。

  **i** 是一个**修饰符** (搜索不区分大小写)。

* #### search() 方法使用正则表达式

  ```
  使用正则表达式搜索 "Runoob" 字符串，且不区分大小写：
  var str = "Visit Runoob!"; 
  var n = str.search(/Runoob/i)
  ```

* #### search() 方法使用字符串

  ```
  search 方法可使用字符串作为参数。字符串参数会转换为正则表达式：
  检索字符串中 "Runoob" 的子串：
  var str = "Visit Runoob!"; 
  var n = str.search("Runoob");
  ```

* #### replace() 方法使用正则表达式

  ```
  var str = document.getElementById("demo").innerHTML; 
  var txt = str.replace(/microsoft/i,"Runoob");
  ```

* #### replace() 方法使用字符串

  ```
  replace() 方法将接收字符串作为参数：
  var str = document.getElementById("demo").innerHTML; 
  var txt = str.replace("Microsoft","Runoob");
  ```

* #### 正则表达式修饰符

  **修饰符** 可以在全局搜索中不区分大小写:

  | i    | 执行对大小写不敏感的匹配。                               |
  | ---- | -------------------------------------------------------- |
  | g    | 执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。 |
  | m    | 执行多行匹配。                                           |

* #### 正则表达式模式

  方括号用于查找某个范围内的字符：

  | [abc]  | 查找方括号之间的任何字符。 |
  | ------ | -------------------------- |
  | [0-9]  | 查找任何从 0 至 9 的数字。 |
  | (x\|y) | 查找任何以 \| 分隔的选项。 |

  元字符是拥有特殊含义的字符：

  | \d     | 查找数字。                                  |
  | ------ | ------------------------------------------- |
  | \s     | 查找空白字符。                              |
  | \b     | 匹配单词边界。                              |
  | \uxxxx | 查找以十六进制数 xxxx 规定的 Unicode 字符。 |

  量词:

  | n+   | 匹配任何包含至少一个 *n* 的字符串。   |
  | ---- | ------------------------------------- |
  | n*   | 匹配任何包含零个或多个 *n* 的字符串。 |
  | n?   | 匹配任何包含零个或一个 *n* 的字符串。 |

  

* #### 使用 RegExp 对象

  在 JavaScript 中，RegExp 对象是一个预定义了属性和方法的正则表达式对象。

* #### 使用 test()

  test() 方法是一个正则表达式方法。

  test() 方法用于检测一个字符串是否匹配某个模式，如果字符串中含有匹配的文本，则返回 true，否则返回 false。

  以下实例用于搜索字符串中的字符 "e"：

  ```
  var patt = /e/;
  patt.test("The best things in life are free!");
  
  字符串中含有 "e"，所以该实例输出为：
  true
  ```

  也可以不用设置正则表达式的变量，以上两行代码可以合并为一行：

  ```
  /e/.test("The best things in life are free!")
  ```

* #### 使用 exec()

  exec() 方法是一个正则表达式方法。

  exec() 方法用于检索字符串中的正则表达式的匹配。

  该函数返回一个数组，其中存放匹配的结果。如果未找到匹配，则返回值为 null。

  以下实例用于搜索字符串中的字母 "e":

  ```
  /e/.exec("The best things in life are free!");
  
  字符串中含有 "e"，所以该实例输出为:
  e
  ```

* #### 正则表达式表单验证实例：

  ```
  /*是否带有小数*/
  function    isDecimal(strValue )  {  
     var  objRegExp= /^\d+\.\d+$/;
     return  objRegExp.test(strValue);  
  }  
  
  /*校验是否中文名称组成 */
  function ischina(str) {
      var reg=/^[\u4E00-\u9FA5]{2,4}$/;   /*定义验证表达式*/
      return reg.test(str);     /*进行验证*/
  }
  
  /*校验是否全由8位数字组成 */
  function isStudentNo(str) {
      var reg=/^[0-9]{8}$/;   /*定义验证表达式*/
      return reg.test(str);     /*进行验证*/
  }
  
  /*校验电话码格式 */
  function isTelCode(str) {
      var reg= /^((0\d{2,3}-\d{7,8})|(1[3584]\d{9}))$/;
      return reg.test(str);
  }
  
  /*校验邮件地址是否合法 */
  function IsEmail(str) {
      var reg=/^\w+@[a-zA-Z0-9]{2,10}(?:\.[a-z]{2,4}){1,3}$/;
      return reg.test(str);
  }
  ```

  