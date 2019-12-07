# 02_005-2  Ajax的无刷新技术

# Ajax 01

### Java中JSON的解析与生成.

```
引入谷歌的 gson.jar (阿里云短信也依赖此jar包)
```

#### 将Java中的对象, 转换为JSON字符串

```
步骤:
    1.  创建GSON对象.
            Gson g = new Gson();

    2.  将需要转换的对象, 转换为字符串
            String text = g.toJson(java对象);
```

#### 将JSON字符串, 转换为Java中的对象

```
前提: JSON格式 与 要转换的对象类型格式必须一致.

步骤:
    1.  创建GSON对象
            Gson g = new Gson();

    2.  将字符串 转换为 指定类型的对象
            类名 对象名 = g.fromJson(JSON格式字符串, 类名.class);

特殊情况:  我们需要转换的JSON数据, 没有可匹配的类.  可以选择将JSON数据 转换为Map集合.
```

## Ajax - JS

### 简介

```
是一种网页异步请求的技术, 用于浏览器与服务器之间异步的交互. 常用于网页局部页面刷新操作.
```

### ajax的使用步骤

#### GET

```
1.  创建一个用于异步请求的对象
        var xhr = new XMLHttpRquest();

2.  设置异步请求的方式, 以及网址和参数
        xhr.open("GET","网址?参数列表");

3.  设置请求状态事件的处理函数
        xhr.onreadystatechange = function(){
            //  通过xhr.readyState 获取请求的状态.
            //  状态值有五个:
            //  0:  正在初始化
            //  1:  请求正在发送
            //  2:  请求发送完毕
            //  3:  服务器正在响应
            //  4:  响应完毕, 连接已断开

4.  判断事件发生时, 状态为4 .
            if(xhr.readyState == 4){
5.  判断服务器的响应状态码(xhr.status) (200/404/500 等等)
                if(xhr.status == 200){
                    //请求成功
6.  成功时, 可以通过xhr.responseText 接收响应体.
                }else{
                    //请求失败, 一般是因为服务器BUG  或 用户网络问题.
                }
            }
        }
7.  发送请求
        xhr.send();
```

#### POST

```
1.  创建一个用于异步请求的对象
        var xhr = new XMLHttpRquest();

2.  设置异步请求的方式, 以及网址
        xhr.open("POST","网址");

3.  设置请求状态事件的处理函数
        xhr.onreadystatechange = function(){
            //  通过xhr.readyState 获取请求的状态.
            //  状态值有五个:
            //  0:  正在初始化
            //  1:  请求正在发送
            //  2:  请求发送完毕
            //  3:  服务器正在响应
            //  4:  响应完毕, 连接已断开

4.  判断事件发生时, 状态为4 .
            if(xhr.readyState == 4){
5.  判断服务器的响应状态码(xhr.status) (200/404/500 等等)
                if(xhr.status == 200){
                    //请求成功
6.  成功时, 可以通过xhr.responseText 接收响应体.
                }else{
                    //请求失败, 一般是因为服务器BUG  或 用户网络问题.
                }
            }
        }
7.  如果需要传递参数, 需要加入POST请求头:
        xhr.setRequestHeader("content-type","application/x-www-form-urlencoded");
8.  发送请求
        xhr.send(参数列表);//参数列表的格式 与 GET请求? 后的参数列表格式一致.
```

# Ajax 02

## Ajax - Jquery

```
jQuery 对 ajax进行了封装, 简化了ajax的开发流程, 并且实现了多浏览器的兼容.
```

### ajax 函数 *

```
函数名称:   $.ajax
参数列表:   只有一个参数,  这个参数是一个规格对象, 描述Ajax请求的规格.

格式:
    $.ajax({
        url:"请求的网址",
        type:"GET或POST",
        async:"请求是否异步",//默认值为true , 表示异步请求
        data:"请求的参数列表",//格式与get请求?后的参数列表一致
        dataType:"TEXT或JSON",//服务器返回的数据类型.
        success:function(data){
            //当服务器响应的状态码在200-299之间时. 表示成功,此函数执行
            //参数data 是服务器回复的响应体.
            //当dataType值为TEXT时, data是string类型的
            //当dataType值为JSON时, data是对象.
        },
        error:function(){
            //当服务器响应的状态码不再200-299之间时, 表示失败, 此函数执行
        }
    });
```

### get函数 与 post函数 ***

```
两个函数的格式一致的 , get函数用于get请求, post函数用于post请求

函数名称: $.get 或 $.post
参数列表:
        参数1.    url : string类型   请求网址
        参数2.    data: string类型      请求的参数 , 格式与get请求后?的格式一致
        参数3.    success: function类型的参数 ,成功时处理的函数.
        参数4.    dataType:  string类型 响应的数据类型, TEXT或JSON
```

### getJSON函数 *

```
函数名称: $.getJSON
参数列表:
        参数1.    url : string类型   请求网址
        参数2.    data: string类型      请求的参数 , 格式与get请求后?的格式一致
        参数3.    success: function类型的参数 ,成功时处理的函数.
```

### load函数 了解

```
作用: 将ajax返回的结果, 直接加载到调用函数的元素中.

函数名称:   jquery对象.load
参数列表:   
        参数1.    url : string类型   请求网址
        参数2[可选].    data: string类型      请求的参数 , 格式与get请求后?的格式一致
        参数3[可选].    success: function类型的参数 ,成功时处理的函数.
```

## Ajax - Vue

```
只有页面是通过Vue编写的情况下, 我们才采用Vue的ajax方案. 
目前绝大多数网页都是 : Vue+bootstrap . 
```

#### 格式:

```
使用vue的ajax 除了必须引入vue.js ,还需要引入vue-resource.js
```

#### 全局ajax函数 (了解)

```
在不创建Vue实例的情况下,  使用全局ajax函数.

GET请求格式:
    Vue.http.get("请求地址",["请求的参数"]).then(success,error);
POST请求格式:
    Vue.http.post("请求地址",["请求的参数"],{"emulateJSON":true}).then(success,error);
```

#### 基于vue实例的 ajax函数

```
在已创建vue实例的情况下, 建议使用基于示例的ajax函数.

GET请求格式:
    this.$http.get("请求地址",["请求的参数"]).then(success,error);
POST请求格式:
    this.$http.post("请求地址",["请求的参数"],{"emulateJSON":true}).then(success,error);
```

#### 上述格式中, 出现的参数写法:

```
1.  请求地址:   string类型的字符串. 相对路径即可.
2.  GET请求的参数:   请求的参数以对象的方式传递. 例如: 我们需要传递username和password, 可以按照如下格式编写:
        var user = new Object();
        user.username = "xxx";
        user.password = "xxx";
        var obj = new Object();
        obj.params = user;
        //传递obj对象即可

        或者:
        {
            params:{
                username:"xxx",
                password:"xxx"
            }
        }

3.  POST请求的参数: 请求的参数以对象的方式传递. 例如: 我们需要传递username和password, 可以按照如下格式编写:
        var user = new Object();
        user.username = "xxx";
        user.password = "xxx";

        或者:
        {
            username:"xxx",
            password:"xxx"
        }

4.  success函数 与 error函数的编写
        success函数 与 error函数编写方法完全一致;
        格式:
            function(res){

            }

        res(响应对象)的常用属性:
            -   url :   响应的网址
            -   body:   响应体 , 如果响应的内容是JSON格式的, 得到的是对象, 如果不是JSON,得到的是string
            -   ok  :   boolean值, 当响应码为200-299之间时, 为true
            -   status  :   响应码: 200 , 404 ,500 等等
            -   statusText : 响应码对应的文字, 例如: 200对应的是ok 

        res(响应对象)的常用函数:
            -   text()  :   以字符串形式, 返回响应体
            -   json()  :   以对象形式, 返回响应体
            -   blob()  :   以大数据二进制形式, 返回响应体.
```

# Ajax 03

### ajax请求同步与异步的区别

* #### 同步请求

  同步：顺序处理，程序向服务器发送一个请求，在结果返回之前，程序要一直等待结果返回才可以执行下一步操作

  ```
  //同步请求
  $.ajax({
      type:'post',
  　url:"<c:url value='/device/org/' />"+val,
  　data:{'orgId':val},
  　success:function(data){//function(1)
  　name=data.orgName;
  　},
  　dataType:"json",
  
  　async:false
  });
  
  function(2);
  ```

  当执行当前AJAX的时候会停止执行后面的JS代码，直到AJAX执行完毕后时，才能继续执行后面的JS代码。

  当把async设为false时，这时ajax的请求时同步的，也就是说，这个时候ajax块发出请求后，他会等待在function1（）这个地方，不会去执行function2()，直到function1()部分执行完毕。

* #### 异步请求

  异步：并行处理，程序向服务器发送一个请求，在结果返回之前，程序还是可以执行其它操作（以前台界面为例，用户依然可以输入其它信息，并且和服务器进行其它交付），大大节省了用户的时间，也提高用户的体验

  ```
  //异步请求
  $.ajax({ 
       type:"POST",
       url:"Venue.aspx?act=init",
       dataType:"html",
       success:function(result){  //function1()
         f1();
         f2(); 
      }
       failure:function (result) { 
        alert('Failed'); 
       },
   }
   function2();
  ```

  当ajax发送请求后，在等待server端返回的这个过程中，前台会继续 执行ajax块后面的脚本，直到server端返回正确的结果才会去执行success，也就是说这时候执行的是两个线程，ajax块发出请求后一个线程 和ajax块后面的脚本（另一个线程）

  在上例中，当ajax块发出请求后，他将停留function1()，等待server端的返回，但同时（在这个等待过程中），前台会去执行function2()。

### ajax跨域问题

* #### 1.什么是跨域？

  跨域：指的是浏览器不能执行其他网站的脚本。它是由浏览器的同源策略造成的，是浏览器对javascript施加的安全限制。

  例如：a页面想获取b页面资源，如果a、b页面的协议、域名、端口、子域名不同，所进行的访问行动都是跨域的，而浏览器为了安全问题一般都限制了跨域访问，也就是不允许跨域请求资源。注意：跨域限制访问，其实是**浏览器的限制**。理解这一点很重要！！！

  同源策略：是指协议，域名，端口都要相同，其中有一个不同都会产生跨域；

  ![img](https://upload-images.jianshu.io/upload_images/9487719-d9eb2035e204d817.png?imageMogr2/auto-orient/strip|imageView2/2/w/717/format/webp)

* #### 2.跨域访问示例

  假设有两个网站，A网站部署在：http://localhost:81 即本地ip端口81上；B网站部署在：http://localhost:82 即本地ip端口82上。现在A网站的页面想去访问B网站的信息，A网站页面的代码如下（这里使用jquery的异步请求）

  > $(function (){
  >
  >   $.get("http://localhost:82/api/values", {},function (result) {
  >
  > ​     $("#show").html(result);
  >
  > ​             })})；

  

  ![img](https:////upload-images.jianshu.io/upload_images/9487719-37852d7e52a95f8a.png?imageMogr2/auto-orient/strip|imageView2/2/w/744/format/webp)

  从错误信息可以看出以上出现了跨域问题！

* #### 3.跨域产生的原因

  （1）浏览器的限制

  （2）跨域，域名不一致，端口不一致

  （3）XHR（XMLHttpRequest）请求

  三个同时存在才有可能产生跨域问题

* #### 4.解决跨域问题的思路

  （1）浏览器（通过指定参数让浏览器不去做校验，需要改动客户端，意义不大）

  （2）XHR（通过修改发出请求的类型，通过JSONP，动态创建script，在script中发送请求）

  （3）跨域

  　	a）修改被调用，让其支持跨域   

  ​		b）修改调用方，隐藏跨域，使用代理

## 复现Ajax跨域问题

- 做两个简单的小项目复现Ajax跨域问题. 后端语言使用Java
- 首先是一个简单的订单系统, 通过访问`/loadOrderList`, 最终以json串形式返回订单集合. 该项目使用Tomcat发布在7070端口.

```
@RequestMapping("/loadOrderList")
@ResponseBody
public List<Order> loadOrderList(String uid){
    //模拟订单数据
    Order o1 = new Order();
    o1.setId("111");
    o1.setTotal(333.33);
    o1.setDate("2019-4-29");

    Order o2 = new Order();
    o2.setId("222");
    o2.setTotal(444.44);
    o2.setDate("2019-5-29");

    Order o3 = new Order();
    o3.setId("333");
    o3.setTotal(555.55);
    o3.setDate("2019-6-29");

    List<Order> list = new ArrayList<>();
    list.add(o1);
    list.add(o2);
    list.add(o3);

    return list;
}
```

- 在另一个项目中做一个向订单系统发送一个ajax请求, 获取订单集合. 该项目使用Tomcat插件发布在9090端口.

```
//index.jsp

<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
    <script type="text/javascript" src="https://code.jquery.com/jquery-1.11.3.js"></script>
    <script type="text/javascript">
        function sendAjax() {
            $.post("http://localhost:7070/order/loadOrderList", "uid=1234", function (data) {
                alert(data);
            });
        }
    </script>
</head>
<body>
    <a href="javascript:sendAjax()">sendAjax</a>
</body>
</html>
```

- 点击`sendAjax`超链接向订单系统发送ajax请求.
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190430191117328.png)
- 通过开发者工具发现虽然服务器以状态码200响应回来, 但是控制台却报错了.
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190430191353533.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTM1Nzc2Nw==,size_16,color_FFFFFF,t_70)
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190430193153869.png)
- 这就是Ajax跨域出错的一种表现, 下面分析原因.

## Ajax跨域介绍

- Ajax跨域问题是由浏览器的同源策略造成的, 首先要理解`源`这个概念.
- 我们可以通过协议+域名+端口确定一个源. 在上面的示例中, 你可以把一个项目理解为一个源. Ajax请求可以对源内的资源发起访问, 但是不同源之间进行Ajax就会有问题.
- 当向不同源的资源发起Ajax请求时, 浏览器会加上`Origin`字段来标识源

```
Accept: */*
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Connection: keep-alive
Content-Length: 8
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
Host: localhost:7070
Origin: http://localhost:9090   协议+域名+端口
```

- 服务器会根据`Origin`字段决定是否同意这次请求, 如果`Origin`指定的源不在许可范围内, 服务器会返回一个不带有`Access-Control-Allow-Origin`字段的响应. 浏览器解析时发现缺少了这个字段, 就会报错. 这种错误不能通过状态码识别, 因为状态码很有可能就是200(见上面的案例).

## Ajax跨域解决方案

- 下面介绍最常用Ajax跨域解决方案.

### 一. 在服务端添加响应头`Access-Control-Allow-Origin`

- 既然我们已经知道了Ajax跨域失败是因为响应中缺少了响应头`Access-Control-Allow-Origin`, 那么就想办法加上去.
- 以Java项目为例, 在后端我们使用`CORSFilter`过滤器加上该响应头.
- (假设是Maven项目), 首先在`pom.xml`中添加坐标

```
<dependency>
    <groupId>com.thetransactioncompany</groupId>
    <artifactId>cors-filter</artifactId>
    <version>2.5</version>
    <scope>runtime</scope>
</dependency>
```

- 然后在`web.xml`中对过滤器进行配置.

```
    <filter>
        <filter-name>CORS</filter-name>
        <filter-class>com.thetransactioncompany.cors.CORSFilter</filter-class>
        <init-param>
            <param-name>cors.allowOrigin</param-name><!--这个标签是关键, *代表所有源都能访问-->
            <param-value>*</param-value>
        </init-param>
        <init-param>
            <param-name>cors.supportedMethods</param-name>
            <param-value>GET, POST, HEAD, PUT, DELETE</param-value>
        </init-param>
        <init-param>
            <param-name>cors.supportedHeaders</param-name>
            <param-value>Accept, Origin, X-Requested-With, Content-Type, Last-Modified</param-value>
        </init-param>
        <init-param>
            <param-name>cors.exposedHeaders</param-name>
            <param-value>Set-Cookie</param-value>
        </init-param>
        <init-param>
            <param-name>cors.supportsCredentials</param-name>
            <param-value>true</param-value>
        </init-param>
    </filter>

    <filter-mapping>
        <filter-name>CORS</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
```

- 配置后重启订单项目, 再次发起Ajax请求可以看到成功返回数据, 响应头中包含了`Access-Control-Allow-Origin`, 值为发起Ajax请求的源.
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190430194918105.png)
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190430195151524.png)

### 二. 使用JSONP解决

- 上面直接通过过滤器添加响应头的方法可以说是对症下药, 那么还有没有什么偏方呢?
- 还真的有. 在jsp文件中经常通过通过``标签引入一段js代码, 这段代码通常来源于网络, 也就是不同源. 那么我们不妨通过``标签完成Ajax请求, 这样便顺带解决了跨域问题.
- 下面还是沿用上面的案例进行演示.
- 我们对发送ajax的jsp进行修改

```
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
    <script type="text/javascript" src="https://code.jquery.com/jquery-1.11.3.js"></script>
    <script>
        function doCallBack(data){
            var str = JSON.stringify(data);
            alert(str);
        }
    </script>
</head>
<body>
    <script src="http://localhost:7070/order/loadOrderList3?uid=111&callBack=doCallBack"></script>
</body>
</html>
```

- 上面的代码中, 我们首先定义了`doCallBack()`函数, 它接收一个字符串参数, 并且会把接收到的字符串显示出来.
- 然后在``标签中编写``标签, 我们将通过``标签请求订单系统, 订单系统将会返回一段js代码, 这段js代码会调用`doCallBack()`方法.
- 为了能够拼接出`doCallBack(字符串参数...)`js代码, 我们在订单系统中作如下操作.

```
@RequestMapping("/loadOrderList3")
@ResponseBody
public String loadOrderList3(String uid, String callBack){
    //模拟订单数据
    Order o1 = new Order();
    o1.setId("111");
    o1.setTotal(333.33);
    o1.setDate("2019-4-29");

    Order o2 = new Order();
    o2.setId("222");
    o2.setTotal(444.44);
    o2.setDate("2019-5-29");

    Order o3 = new Order();
    o3.setId("333");
    o3.setTotal(555.55);
    o3.setDate("2019-6-29");

    List<Order> list = new ArrayList<>();
    list.add(o1);
    list.add(o2);
    list.add(o3);

    //拼接js代码
    String result = callBack + "(" + JSON.toJSONString(list) + ")";
    return result;
}
```

- 这个想法是不是很妙? 明白这个原理之后, 我们可以使用jQuery方便进行JSONP操作, 在上面的代码中我们人为指定了一个名为`doCallBack`的函数, 而jQuery会随机用时间戳生成一个函数名, 原理和上面是一样的.
- 所以完成一开时点击超链接发送Ajax请求只需要如下几步.

```
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
    <script type="text/javascript" src="https://code.jquery.com/jquery-1.11.3.js"></script>
    <script>
        function sendAjax(){
            $.getJSON("http://localhost:7070/order/loadOrderList3?callBack=?","uid=111",
            function (data) {
                var str = JSON.stringify(data);
                alert(str);
            });
        }
    </script>
</head>
<body>
    <a href="javascript:sendAjax()">sendAjax</a>
</body>
</html>
```

### 小结

- 上面两种解决办法在思路上有着本质的不同. 方案一抓住`CORS`跨域访问问题的本质, 在后端加上响应头解决跨域问题. 方案二`JSONP`利用的是``标签能够跨域获取js代码的特性, 绕过跨域问题.

### 参考文献

ajax跨域问题https://www.cnblogs.com/zhyue93/p/ajax.html

AJAX的出现与跨域处理https://segmentfault.com/a/1190000013072204

详细解析JS中Ajax的使用技巧https://www.php.cn/js-tutorial-394117.html

Ajax跨域问题及解决方案https://www.cnblogs.com/tanshaoshenghao/p/10799042.html

AJAX跨域完全讲解https://www.cnblogs.com/Java3y/p/8490439.html

