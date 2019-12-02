# Bootstrap 框架

2019/11/1 8:36:37 

------

### 简介

```
Bootstrap是由Twitter 的两名前端程序员 研发的.
是一套基于HTML / CSS / JS 的前端开源框架.

bootstrap 擅长响应式网页的开发, 我们可以使用它很简单的构建出适用于 PC 以及 移动端的网页.
```

### 使用步骤:

```
1.  下载bootstrap 框架文件
2.  解压后 得到三个文件夹:
        -   css     :   样式文件
        -   fonts   :   样式文件中使用的字体文件
        -   js      :   脚本文件

3.  编写HTML , 引入相应的框架文件

4.  先引入jquery
    <script src="js/jquery.js"></script>
5.  引入bootstrap.min.js
    <script src="js/bootstrap.min.js"></script>
6.  引入bootstrap.css
    <link rel="stylesheet" type="text/css" href="css/bootstrap.css">
```

### 常用 class

#### 文本对齐方式

```
class:
    -   text-left:  内容居左
    -   text-center:    内容居中
    -   text-right: 内容居右
```

#### 列表样式

```
class:
    -   list-unstyled   :   取消前置的文字 或 图标. 并取消左内边距
    -   list-inline     :   取消前置的文字 或 图标. 并取消左内边距, 并设置所有的li 为行内元素 横向排列
```

#### 代码块样式

```
原样显示块:  <pre></pre>
bootstrap代码块:  给div指定class="well"
```

#### 前景后景色

```
前景色 (文本颜色)
    class   :   
        -   text-muted  :   柔和灰
        -   text-info   :   信息蓝
        -   text-primary:   主要蓝
        -   text-success:   成功绿
        -   text-warning:   警告黄
        -   text-danger :   危险红

后景色 (背景颜色)
    有些特殊的后景色,  在使用时因为颜色较深, #333的文字颜色无法正常的显示, 会自动设置前景色为白色.
    class   :
        -   bg-info :   信息蓝
        -   bg-primary: 主要蓝
        -   bg-success: 成功绿
        -   bg-warning: 警告黄
        -   bg-danger : 危险红
```

#### 表格样式

##### 基本表格样式

```
table标签 : class=table
```

##### 条纹表格样式

```
table标签 : class=table table-striped
```

##### 边框表格样式

```
table标签 : class=table table-bordered
```

##### 鼠标移入激活表格样式

```
table标签 : class=table table-hover
```

##### 单独指定tr样式

```
tr标签添加class:
    -   active  :   激活样式 , 半透明的灰色
    -   success :   成功绿
    -   info    :   信息蓝
    -   warning :   警告黄
    -   danger  :   危险红
    -   sr-only :   隐藏tr
```

##### 文字图标

```
使用步骤:
    1.  编写span
    2.  给span设置class
    3.  例如:
            <span class="glyphicon glyphicon-heart"></span>
```

![img](https://i.imgur.com/CVh9STU.png)

#### 按钮样式

##### 按钮颜色

```
class   :
    -   btn btn-default :   默认按钮
    -   btn btn-success :   成功绿按钮
    -   btn btn-info    :   信息蓝按钮
    -   btn btn-warning :   警告黄按钮
    -   btn btn-danger  :   危险红按钮
    -   btn btn-link    :   超链接样式按钮

可以应用到如下几种元素上:
    1.  input标签
    2.  button标签
    3.  超链接a标签 推荐
    4.  span标签 推荐
```

##### 按钮尺寸

```
class:
    -   btn-lg  :   大按钮
    -   btn-sm  :   小按钮
    -   btn-xs  :   超小按钮
    -   btn-block:  块按钮 , 横向占满一行的按钮
```

##### 激活与禁用

```
class:
    -   active  :   激活
    -   disabled:禁用
```

#### 输入框样式

##### 块输入框

```
class   :   from-control
```

##### 内联输入框

```
步骤:
    1.  给form标签, 添加class="form-inline"
    2.  给input标签, 添加class="form-control"

是响应式的, 当屏幕宽度小于768px时 , 会转换为块输入框.
```

##### 输入框 尺寸

```
class:
    -   input-lg    :   大输入框
    -   input-sm    :   小输入框
```

#### 移动设备优先

```
我们编写的网页, 在手机端打开时, 视觉效果 缩小了很多倍.
可以通过如下的meta  来设置手机显示时自动适应, 缩放到适用于用户浏览的像素级别.

通常手机端缩放以后, 宽度是小于768px的

自适应大小:
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1">

自适应大小, 并禁止用户缩放
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
```

### 响应式

#### 栅格系统

```
栅格系统, 将屏幕按照像素分辨率的不同, 分为了四种屏幕 (超小屏幕, 小屏幕, 中等屏幕 ,大屏幕)
栅格可以按照不同的屏幕规格, 来调整元素的内容的宽度.
栅格系统, 将屏幕横向分为了 12等份.
```

##### 栅格容器

```
使用栅格,  需要将栅格的内容, 都编写在栅格容器中.
容器分为两种: 
    1.  固定宽度的容器
            屏幕种类:       超小屏幕        小屏幕             中等屏幕                大屏幕
            屏幕规格:       小于768px 768px≤屏幕＜992px  992px≤屏幕＜1200px         1200px≤屏幕
            栅格宽度固定值:    100%        750px               970px               1170px

            格式: <div class="container"></div>

    2.  撑满父元素的容器.
            格式: <div class="container-fluid"></div>
```

##### 栅格行

```
栅格容器中的内容, 必须编写在栅格行中.
栅格行横向可以被分为12等份 , 一行排满12份后, 换行显示.

格式: 
    <div class="row"></div>
```

##### 栅格列的指定方式

```
每种屏幕规格下, 都有12个不同的class , 用来描述占用的分为 1-12

为了便于记忆, class值有规律, 每种屏幕规格, 前缀相同.

格式:
    屏幕种类:       超小屏幕            小屏幕             中等屏幕                大屏幕
    类前缀:            col-xs-数字   col-sm-数字           col-md-数字           com-lg-数字

上述格式中的数字,是1-12的范围, 表示此规格下, 占用的栅格份数.
```

##### 栅格偏移

```
class:
    类前缀-offset-数字 : 元素向右偏移指定格
```

#### 显示与隐藏

```
    屏幕种类:           超小屏幕        小屏幕             中等屏幕                大屏幕
    屏幕规格:           小于768px 768px≤屏幕＜992px  992px≤屏幕＜1200px         1200px≤屏幕

    显示class:
    visible-xs-参数       显示          隐藏                  隐藏                  隐藏
    visible-sm-参数       隐藏          显示                  隐藏                  隐藏
    visible-md-参数       隐藏          隐藏                  显示                  隐藏
    visible-lg-参数       隐藏          隐藏                  隐藏                  显示
    注:  上述的参数, 指的是元素以什么分类显示, 可选的值:inline / inline-block / block


    隐藏class:
    hidden-xs           隐藏          显示                  显示                  显示
    hidden-sm           显示          隐藏                  显示                  显示
    hidden-md           显示          显示                  隐藏                  显示
    hidden-lg           显示          显示                  显示                  隐藏
```

### 导航栏

```
步骤:
    1.  编写ul标签  class="nav nav-tabs"
    2.  给 ul添加 子标签li , li的内容必须被a标签包含.

案例:

    <ul class="nav nav-tabs">
        <li><a>首页</a></li>
        <li><a>欧美</a></li>
        <li><a>日韩</a></li>
        <li><a>亚洲</a></li>
        <li class="active"><a>非洲大**</a></li>
        <li><a>更多</a></li>
    </ul>
```

### 导航+内容切换

```
步骤:
    1.  编写一个导航栏 
    2.  在网页中编写一个div , 用于显示内容. 并指定div的class="tab-content"
    3.  给上述的div 添加多个子div . 每一个子div 绑定导航中的一个选项. 就是每一个选项显示的内容.
    4.  给每一个子div ,添加id , 并指定class="tab-pane fade" , 默认显示的子div ,class="tab-pane fade in active"
    5.  修改导航栏中的a标签, 添加属性:data=toggle="tab" href="#子div的id"
    6.  给默认的li ,设置激活效果 class="active"


案例:

    <ul class="nav nav-tabs">
        <li class="active"><a href="#tab1" data-toggle="tab">首页</a></li>
        <li><a href="#tab2" data-toggle="tab">欧美</a></li>
        <li><a href="#tab3" data-toggle="tab">日韩</a></li>
        <li><a href="#tab4" data-toggle="tab">亚洲</a></li>
        <li><a href="#tab5" data-toggle="tab">非洲大**</a></li>
        <li><a href="#tab6" data-toggle="tab">更多</a></li>
    </ul>

    <div class="tab-content">
        <div id="tab1" class="tab-pane fade in active">
            <h1>网站首页</h1>
            <h3>锄禾日当午, 汗滴禾下土.</h3>
        </div>
        <div id="tab2" class="tab-pane fade">
            <h3>欧美资源页</h3>
            <img src="images/29.jpg">
        </div>
        <div id="tab3" class="tab-pane fade">
            <h3>日韩资源页</h3>
            <img src="images/30.jpg">
        </div>
        <div id="tab4" class="tab-pane fade">
            <h3>亚洲资源页</h3>
            <img src="images/28.jpg">
        </div>
        <div id="tab5" class="tab-pane fade">
            <h3>大**资源页</h3>
            <img src="images/31.jpg">
        </div>
        <div id="tab6" class="tab-pane fade">
            <h3>更多资源请登录</h3>
        </div>

    </div>
```