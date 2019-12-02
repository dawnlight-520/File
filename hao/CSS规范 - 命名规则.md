## CSS规范 - 命名规则

- 使用类选择器，放弃ID选择器

  ​                            ID在一个页面中的唯一性导致了如果以ID为选择器来写CSS，就无法重用。                        

- NEC特殊字符："-"连字符

  ​                            "-"在本规范中并不表示连字符的含义。                            她只表示两种含义：分类前缀分隔符、扩展分隔符，详见以下具体规则。                        

- 分类的命名方法：使用单个字母+"-"为前缀

  ​                            布局（grid）（.g-）；模块（module）（.m-）；元件（unit）（.u-）；功能（function）（.f-）；皮肤（skin）（.s-）；状态（.z-）。                            对以上的解释详情参见：[分类方法](http://nec.netease.com/standard/css-sort.html)中的“CSS内部的分类及其顺序”。                            注：在你样式中的选择器总是要以上面前五类开头，然后在里面使用后代选择器。                            　　如果这五类不能满足你的需求，你可以另外定义一个或多个大类，但必须符合单个字母+"-"为前缀的命名规则，即 .x- 的格式。                            　　特殊：.j-将被专用于JS获取节点，请勿使用.j-定义样式。                        

- 后代选择器命名

  ​                                                            约定**不以单个字母+"-"为前缀**且长度大于等于2的类选择器为后代选择器，如：.item为m-list模块里的每一个项，.text为m-list模块里的文本部分：.m-list .item{}.m-list .text{}。                                一个语义化的标签也可以是后代选择器，比如：.m-list li{}。                                *不允许单个字母的类选择器*出现，原因详见下面的“模块和元件的后代选择器的扩展类”。                                                        通过使用后代选择器的方法，你不需要考虑他的命名是否已被使用，因为他只在当前模块或元件中生效，*同样的样式名可以在不同的模块或元件中重复使用*，互不干扰；在多人协作或者分模块协作的时候效果尤为明显！                            后代选择器不需要完整表现结构树层级，*尽量能短则短。*                            注：后代选择器*不要在页面布局中使用*，因为污染的可能性较大； `/* 这里的.itm和.cnt只在.m-list中有效 */``.m-list{``margin``:``0;``padding``:``0;``}``.m-list .itm{``margin``:``1px``;``padding``:``1px``;}``.m-list .cnt{``margin-left``:``100px``;}``/* 这里的.cnt和.num只在.m-page中有效 */``.m-page{``height``:``20px``;}``.m-page .cnt{``text-align``:``center``;}``.m-page .num{``border``:``1px` `solid` `#ddd``;}`                        

- 命名应简约而不失语义

   `/* 反对：表现化的或没有语义的命名 */``.m-abc .green2{}``.g-left2{}``/* 推荐：使用有语义的简短的命名 */``.m-list .wrap2{}``.g-side2{}`                        

- 相同语义的不同类命名

  ​                            方法：直接加数字或字母区分即可（如：.m-list、.m-list2、.m-list3等，都是列表模块，但是是完全不一样的模块）。                            其他举例：.f-fw0、.f-fw1、.s-fc0、.s-fc1、.m-logo2、.m-logo3、u-btn、u-btn2等等。                        

- 模块和元件的扩展类的命名方法

  ​                            当A、B、C、...它们类型相同且外形相似区别不大，那么就以它们中出现率最高的做成基类，其他做成基类的扩展。                            方法：+“-”+数字或字母（如：.m-list的扩展类为.m-list-1、.m-list-2等）。                            补充：基类自身可以独立使用（如：class="m-list"即可），扩展类必须基于基类使用（如：class="m-list m-list-2"）。                            如果你的扩展类是表示不同状态，那么你可以这样命名：u-btn-dis，u-btn-hov，m-box-sel，m-box-hov等等，然后像这样使用：class="u-btn u-btn-dis"。                            如果你的网站可以不兼容IE6等浏览器，那么你标识状态的方法也可以采取独立状态分类（.z-）方法：.u-btn.z-dis，.m-box.z-sel，然后像这样使用：class="u-btn z-dis"。                        

- 模块和元件的后代选择器的扩展类

  ​                            有时候模块内会有些类似的东西，如果你没有把它们做成元件和扩展，那么也可以使用后代选择器和扩展。                            后代选择器：.m-login .btn{}。                            后代选择器扩展：.m-login .btn-1{}，.m-login .btn-dis{}。                            同样也可以采取独立状态分类（.z-）方法：.m-login .btn.z-dis{}，然后像这样使用：class="btn z-dis"。                            注：此方法用于类选择器，直接使用标签做为选择器的则不需要使用此命名方法。                            注：为防止后代选择器的扩展类和大类命名规范冲突，后代选择器不允许使用单个字母。                            　　比如：.m-list .a{}是不允许的，因为当这个.a需要扩展的时候就会变成.a-bb，这样就和大类的命名规范冲突。                        

- 分组选择器有时可以代替扩展方法

  ​                            有时候虽然两个同类型的模块很相似，但是你希望他们之间不要有依赖关系，也就是说你不希望使用扩展的方法，那么你可以通过合并选择器来设置共性的样式。                            使用本方法的前提是：相同类型、功能和外观都相似，写在同一片代码区域方便维护。 `/* 两个元件共性的样式 */``.u-tip1,.u-tip2{}``.u-tip1 .itm,.u-tip2 .itm{}``/* 在分别是两个元件各自的样式 */``/* tip1 */``.u-tip1{}``.u-tip1 .itm{}``/* tip2 */``.u-tip2{}``.u-tip2 .itm{}`                        

- 防止污染和被污染

  ​                            当模块或元件之间互相嵌套，且使用了相同的标签选择器或其他后代选择器，那么里面的选择器就会被外面相同的选择器所影响。                            所以，如果你的模块或元件可能嵌套或被嵌套于其他模块或元件，那么要慎用标签选择器，必要时采用类选择器，并注意命名方式，可以采用.m-layer .layerxxx、.m-list2 .list2xxx的形式来降低后代选择器的污染性。                        

无序列表 ul

在上述的两个列表标签中, li标签表示列表中的一行数据.

案例:
	<h3>有序列表</h3>
	<ol>
		<li>床前明月光 , </li>
		<li>地上鞋一堆 !</li>
		<li>床上马帅兵 ,</li>
		<li>喊十块一双 !</li>
	</ol>
	<h3>无序列表</h3>
	<ul>
		<li>床前明月光 , </li>
		<li>地上鞋一堆 !</li>
		<li>床上马帅兵 ,</li>
		<li>喊十块一双 !</li>
	</ul>

####表格标签

在网页中编写表格标签, 通过三个标签来完成:

	1.	表格本身:	table
	2.	表格中的行:	tr
	3.	行中的列:	td (表头列为th)

属性:
	-	width:	设置table/td的宽度 ,设置td宽度时, 会导致所有行的当前列的宽度变化
	-	height: 设置table/td的高度 ,设置td高度时, 会导致当前行的行高发生改变.
	-	border:	数字值 , 边框的宽度,默认值为0, 单位是px
	-	bordercolor: 边框颜色
	-	bgcolor: 设置table/td的背景颜色
	-	background:设置table/td的背景图片.

代码案例:

	<h3>表格标签 - 用户表格</h3>
	<table border="1" width="100%" height="300px">
		<tr><th>编号</th><th>帐号</th><th>密码</th><th>昵称</th><th>注册时间</th></tr>
		<tr><td>1</td><td>hahaha1</td><td>******</td><td>dsb帅兵</td><td>2019-10-18</td></tr>
		<tr><td>2</td><td>hahaha2</td><td>******</td><td>dsg帅兵</td><td>2019-10-18</td></tr>
		<tr><td>3</td><td>hahaha3</td><td>******</td><td>xsb帅兵</td><td>2019-10-18</td></tr>
		<tr><td>4</td><td>hahaha4</td><td>******</td><td>xsg帅兵</td><td>2019-10-18</td></tr>
		<tr><td>5</td><td>hahaha5</td><td>******</td><td>heiheihei帅兵</td><td>2019-10-18</td></tr>
	</table>
###表单标签 form ***

	简介:	用于显示与收集用户的信息, 并将信息发送给服务器.
	
	常见用途:	
		1.	用户的登录注册.
		2.	搜索引擎
		3.	商城网站的商品检索
		4.	站内检索
		5.	调查问卷 
			等等
	
	常用属性:
		-	action	:	提交的服务器地址.
		-	method	:	提交数据的方式 (GET / POST ...)
						GET(默认)	:	表单中填写的数据,通过网址提交! 数据按照键值对的方式存储在网址的?后.
						POST		:	表单中填写的数据,通过单独的请求体数据包 发送给服务器.


###表单中常用的子标签  input 标签 ***

	输入组件 , 用于接收用户的输入.
	在表单提交时, 输入组件的内容 会以键值对的方式 发送给服务器.
	
	属性:
		-	name	:	输入组件的名称, 在数据提交时,是键值对的 键.
		-	value	:	输入组件的内容, 在数据提交时,是键值对的 值. 当输入组件的形态为输入框时, value也是输入框中的内容
		-	placeholder : 当输入组件的形态为输入框,  用于提示用户输入.
		-	checked	:	输入组件为单选/复选框时 , 默认选中. HTML5boolean属性. 属性存在即为true
	
	输入框的形态:
		type属性: 属性值是输入框的各种形态:
			-	text	:	默认值 , 文本输入框.
			-	password:	密码输入框
			-	number	:	数字输入框.
			-	color	:	颜色调色板
			-	radio	:	单选框 , 一组单选框只能选中一个. 通过相同的name属性来分组.
			-	checkbox:	复选框
			-	file	:	文件上传选择框
			
			日期类型的输入组件形态:
				-	date	:	年月日选择框
				-	month	:	年月选择框
				-	week	:	年周选择框
				-	time	:	时间选择框
				-	datetime:	年月日时分选择框 (大多浏览器已经不支持了.)
				-	datetime-local	:	本地时区的  年月日时分选择框.
				
			按钮类型的输入组件形态:
				-	button	:	普通按钮 *
				-	reset	:	重置按钮, 点击后会导致表单所有内容重置.
				-	submit	:	提交按钮 *
				-	image	:	作用与submit一致, 不过此按钮不展示文字, 而是通过src属性展示图片.
	
			隐藏的输入组件:
				-	hidden	:	隐藏的输入框, 用于隐式的收集用户的信息.


### 表单中常用子标签 select 和 option 掌握

	select	:	下拉选择框
		属性:	
			name属性, 提交数据时的key
	
	option	:	选项
		value属性:	当用户选中后, 提交数据的值

###label标签 了解

	用于事件传递的标签. 
	
	使用步骤:
		1.	给接收事件的元素, 添加id属性值. 
		2.	给产生事件的冤死, 外层嵌套一个label , 并指定 for属性值: 接收事件元素的id


###导航页案例

	<h1><center>xxx导航页</center></h1>
	<h3><center>常用搜索</center></h3>
	<form action="https://www.baidu.com/s">
		<center>
			<input name="wd" placeholder="请输入要百度的内容"><input type="submit" value="百度一下">
		</center>
	</form>
	<form action="http://search.dangdang.com">
			<input name="key" placeholder="请输入要搜索的图书名"><input type="submit" value="搜索图书">
	</form>
	<form action="https://v.qq.com/x/search/">
			<input name="q" placeholder="请输入要搜索的视频"><input type="submit" value="搜索视频">
	</form>
	<form action="https://search.jd.com/Search">
			<input name="enc" value="utf-8" type="hidden">
			<input name="keyword" placeholder="请输入要搜索的商品"><input type="submit" value="京东一下">
	</form>
	<h3><center>常用网址</center></h3>
	<center>
	<table width="80%" height="400px">
		<tr>
			<td><a href="http://4399.com">4399</a></td>
			<td><a href="http://7k7k.com">7k7k</a></td>
			<td><a href="http://xiaowangzhan.com">嘿嘿你懂</a></td>
			<td><a href="#">常用网址1</a></td>
			<td><a href="#">常用网址1</a></td>


###DIV 与 SPAN标签  ***

	DIV:	块元素
	SPAN:	行内元素

###网页碎片化开发 了解

	iframe 框架标签 , 作用: 用于将一个网页引入到当前的页面中
	
	属性:
		-	src	引入的网页地址
		-	height	:引入的网页的窗口的高度
		-	width	:引入的窗口的宽度.

##CSS

###简介

	层叠 cascading 样式 style 表 sheets 
	
	用于调整HTML元素的样式, 通常存储在.css文件中.
	
	优点:	让网页内容 与 网页的样式 完全分离, 提高了代码的复用性 和 维护性 以及 可扩展性.

###样式

	样式表中 包含一个个的样式.
	每一个样式, 就是样式表中的一个键值对.
	格式:
		键与值之间通过冒号连接.
		多个键值对之间通过分号分割.
	
	常见的样式:
		1.	字体大小:	font-size:长度+单位;
		2.	文本颜色:	color:颜色值;
		3.	文字位置:	text-align:left/center/right;
		4.	元素宽度:	width:长度+单位;
		5.	元素高度:	height:长度+单位;
		6.	背景颜色:	background-color:颜色值;
		7.	背景图片:	background-image:url("图片地址");


###CSS的三种使用方式 *****

	1.	内联样式表
			定义在 每一个元素的style属性中.
			案例:	<div style="color:red;font-size:50px;">床前明月光, 地上鞋两双.</div>
	2.	内部样式表
			定义在网页的style标签中, style标签通常编写在head标签中.
			案例:
				<style>
					div{
						text-align: center;
					}
					#div1{
						font-size:12px;
					}
					.c1{
						background-color: #000;
						color:#fff;
					}
				</style>
	3.	外部样式表 ( 推荐 )
			定义在独立的css文件中, 在html的head里通过link标签 引入css文件.
			css文件:
				@charset "UTF-8";
				#div1{
					color:#999;
				}
			link标签:
				<link rel="stylesheet" type="text/css" href="css/demo1.css">

###CSS选择器 

	作用:	用于将样式给定到选择的一个或一组元素 !

####基本选择器 *****

#####元素名称选择器

	作用:	通过元素的名称, 选择一组元素, 将样式给定.
	
	格式:
		元素名称{
			样式列表;
		}

#####id选择器
	作用:	通过元素的id, 选择一个元素, 将样式给定.
	

	格式:
		#id值{
			样式列表;
		}
	
	注意:	HTML规则是松散的, 所以id值可以重复.

#####类选择器

	作用:	通过元素的class属性值, 来选择一组元素, 将样式给定.
	
	格式:
		.class值{
			样式列表;	
		}
	
	注意:	每一个元素都可以设置class属性值, 值的作用是将元素分类!
			每一个元素都可以设置多个class值, 编写格式: class="值1 值2 值3... 值n"

###CSS样式的三大特性 *****

	-	继承性
			部分父元素的样式, 会被子元素继承 !
	-	层叠性
			对于同一个元素, 通过多种方式添加的样式, 不冲突的部分 可以叠加. 冲突的部分参考优先级特性.
	-	优先级
			样式定义来源优先级:
				1.	内联样式 , 优先级最高.
				2.	相同选择器的情况下 , 定义距离body较近的内部样式表 或 外部样式表.
				3.	浏览器默认样式.
				4.	继承得到的样式.


			选择器优先级:
				在内部样式表和外部样式表中 , 不同选择器的优先级不同:
					1.	id选择器			100
					2.	类选择器			10
					3.	元素名称选择器	1
	
			绝对优先样式:
				在样式值的后面, 加入绝对优先关键字: !important;


###伪类选择器
	
####鼠标悬停选择器 *

	作用:	当鼠标悬停在元素上方时 , 样式生效! 鼠标离开元素后 , 样式还原!
	
	格式:
		选择器:hover{
			样式列表;
		}

####获取焦点 选择器

	作用:	当输入组件正在被用户操作时, 样式生效.  失去焦点后 ,样式还原.
	
	格式:
		选择器:focus{
			样式列表;
		}


###组合选择器 熟悉

	优先级权重 计算方式为:  组合中所有选择器 权重的和.

####选择器组

	通过多个选择器, 组合起来锁定一个或多个元素. (当多个选择器都满足时, 样式生效.)
	
	格式:
		元素名称选择器选择器1选择器2...选择器n{
			样式列表;
		}


####选择器列表

	将一组样式, 给定到多个选择器的结果上. (当任意一个选择器满足, 样式就生效)
	
	格式:
		选择器1,选择器2,...选择器n{
			样式列表;
		}

###派生选择器 * 

####子选择器
	格式:
		选择器1>选择器2{

		}
	
	作用:
		从选择器1选的元素中 , 寻找满足选择器2的子元素.
	
	例如:
		选择器id为div1的元素的  id为heihei的子元素
			#div1>#heihei{
	
			}

####后代选择器
	

	格式:
		选择器1 选择器2{
	
		}
	
	作用:
		从选择器1选的元素中 , 寻找满足选择器2的后代元素.
	
	例如:
		选择器id为div1的元素的  id为heihei的后代元素
			#div1 #heihei{
	
			}

###常用样式

####背景样式

	-	背景颜色 *
			background-color:颜色值;
	-	背景图片 *
			background-image:url("图片地址1"),url("图片地址2")...;
			多个图片堆叠显示 , 堆叠的顺序是: URL定义的越靠前, 显示时越靠上.
	
	-	背景图片的控制 - 平铺   (了解)
			background-repeat:
				-	repeat	;	默认值平铺
				-	repeat-x	;	仅横向值平铺
				-	repeat-y	;	仅纵向平铺
				-	no-repeat	;	不平铺
	
	-	背景图片的控制 - 缩放   (了解)
			background-size:宽度% 高度%;
	
	-	背景图片的控制 - 滑动   (了解)
			background-attachment:
				-	scroll	:	滑动, 默认效果.
				-	fixed	:	固定
	
	-	背景图片的控制 - 定位 掌握 
			常用于CSS精灵图片
			格式:
	
			background-position:x偏移值 y偏移值;


​	文字样式

	-	字体大小
			font-size:长度+单位;
	-	文字颜色
			color:颜色值;
	-	内容横向位置
			text-align:left/center/right;
	-	内容纵向位置:
			vertical-align:
				-	top		:	顶部对齐
				-	middle	:	中间对齐
				-	bottom	:	底部对齐
				-	text-top:	文字顶部对齐.
				-	text-bottom:	文字底部对齐
	
	-	文本样式 (斜体)
			font-style:oblique;
	-	文字加粗
			font-weight:bold;
	-	文字修饰
			text-decoration:
				-	underline	:	下划线
				-	overline	:	上划线
				-	line-through:	删除线
	
	-	文本行高(设置一行文本的高度)
			line-height:长度+单位;
			注意:	文本行高等于元素高度时, 一行文字相当于垂直居中
	-	字体设置:
			font-family:字体名称;
	
	-	CSS3版本 安装临时字体 (只在当前页面生效)
			步骤:
				1.	安装字体
					@font-face{
						font-family:自定义字体名称;
						src:url("字体地址");
					}
				2.	使用安装的字体
					选择器{
						font-family:字体名称;
					}
	
	-	文字阴影
			text-shadow:x偏移 y偏移 [阴影模糊距离] 阴影颜色;

### 边框 *

	边框不占用元素的宽高. 
	
	格式1:
		一次指定四个方向的边框 (宽度+样式+颜色)
		border:宽度 样式 颜色值;
	
	格式2:
		单独指定某一个方向边框的宽度 / 样式 / 颜色.
		左:	border-left:宽度 样式 颜色值;
		上:	border-top:宽度 样式 颜色值;
		右:	border-right:宽度 样式 颜色值;
		下:	border-bottom:宽度 样式 颜色值;


	边框样式:
		-	实现	:	solid
		-	虚线	:	dashed
		-	点 	:	dotted

### 边框圆角 

	格式1.	
		一次指定四个角的圆角宽度值.
		border-radius:长度+单位;
	
	格式2.
		单独指定每个角的圆角宽度值.
		上左:	border-top-left-radius:长度+单位;
		上右:	border-top-right-radius:长度+单位;
		下左:	border-bottom-left-radius:长度+单位;
		下右:	border-bottom-right-radius:长度+单位;
	
	边框宽度值 支持百分比, 表示占用元素宽和高的百分比

### 边框阴影

​	格式:
​		box-shadow:x偏移 y偏移 [阴影模糊大小] 阴影大小 阴影颜色;

###处理溢出边框的内容
	

	格式:
		overflow:
			-	visible	:	默认值 , 溢出显示.
			-	hidden	:	溢出隐藏		*
			-	scroll	:	添加滚动条
			-	auto	:	当溢出时, 自动添加滚动条	

### 表格的边框双线问题

	设置给 table 如下的样式:
		border-collapse:collapse;

### CSS盒模型 ( 框模型 ) ***

	指的是元素在网页中 占用空间大小 的计算模型.
	
	占用的宽度的空间:
		元素自身宽度+左右边框宽度+左右内边距+左右外边距.
	
	占用的高度的空间:
		元素自身高度+上下边框宽度+上下内边距+上下外边距.

### 内边距 padding ***

	指的是元素的内容 距离 自身边框的距离.
	
	格式1.
		一次指定四个方向的内边距
		padding:长度+单位;
	
	格式2.
		通过一个样式, 分别指定上下 和 左右的内边距.
		padding: 上下内边距 左右内边距;
	
	格式3.
		通过一个样式, 分别指定 上,右,下,左的内边距
		padding:上 右 下 左;
	
	格式4.
		单独指定每一个方向的内边距
		左:	padding-left:长度+单位;
		右:	padding-right:长度+单位;
		上:	padding-top:长度+单位;
		下:	padding-bottom:长度+单位;

### 外边距 margin ***

	指的是元素的边框 距离 其他元素 盒模型的距离. 值可以是负数.
	
	格式1.
		一次指定四个方向的外边距
		margin:长度+单位;
	
	格式2.
		通过一个样式, 分别指定上下 和 左右的外边距.
		margin: 上下外边距 左右外边距;
	
	格式3.
		通过一个样式, 分别指定 上,右,下,左的外边距
		margin:上 右 下 左;
	
	格式4.
		单独指定每一个方向的外边距
		左:	margin-left:长度+单位;
		右:	margin-right:长度+单位;
		上:	margin-top:长度+单位;
		下:	margin-bottom:长度+单位;

### 外边距的特殊使用方式: 了解

	1.	可以通过指定左右外边距的值 为 auto , 来实现自动居中.
	2.	两个块元素之间, 上下外边距不会累加. 值较大者生效.
	3.	外边距可以设置负数

### 鼠标形状 * 

	cursor	:
		-	default	:	默认鼠标形状,  跟随场景自动变化.
		-	pointer	:	手指形状 , 常用于提示用户 元素可点击.
		-	text	:	焦点形状(工字形)
		-	wait	:	等待
		-	help	:	帮助
		-	progress:	进行中	

### 列表样式 * 

	取消列表前置的数字 或 小圆点.
	
	list-style-type:none;

### 透明度 *

	opacity:0-1的浮点数字.
	当值为1时, 表示不透明.
	当值为0时, 表示完全透明.
	当值为0.5时 , 半透明.

## 定位 *********

	用于控制元素在网页中显示的位置 

#### 默认定位 ( 静态定位 ) *****

	默认定位情况下, 元素分为三类:
		1.	块元素:		独占一行, 可以设置宽度和高度.	例如: div , p ,ul ,ol ,li 等等
		2.	行内元素:	与其它元素共享一行, 从左至右排列. 一行排满时自动换行. 宽度和高度无法设置, 由内容撑开. 例如: span,b,i等等
		3.	行内块元素:	与其它元素共享一行, 从左至右排列, 一行排满时自动换行, 可以设置宽度和高度, 例如: img, button ,input等等
	
	在默认定位情况下,  通过display样式, 调整元素的显示分类:
		display:
			-	block			:	块元素
			-	inline			:	行内元素
			-	inline-block	:	行内块元素
			-	none			:	不显示.

#### 浮动定位 掌握

	格式:	
		float:left/right;
	
	浮动已经脱离了原有的默认定位方式. 
	浮动极易引起周围元素的 显示错乱.
	
	清除浮动带来的影响:
		控制元素的某个方向不允许出现浮动:
		clear:left/right/both;

#### 相对定位

	作用: 元素相对于自身当前位置, 进行x和y轴的移动.
	
	格式:
		position:relative;
	
	特点:
		元素偏移后, 依然占用原有的网页空间, 偏移后的元素 采用覆盖方式显示.

#### 绝对定位

	作用: 根据body的边框, 来确定自身的位置;
		  如果元素存在一个 设置了相对/绝对/固定定位的 祖先元素 .  就变成了根据这个祖先元素的边框来确定自身的位置;
	
	格式:
		position:absolute;
	
	特点:
		元素不再占用任何的网页空间 ,采用覆盖显示.

#### 固定定位

	作用:	根据浏览器的边框, 来固定自身的位置. 不会因为内容的滑动而滑动
	
	格式:	
		position:fixed;
	
	特点:
		 不占用网页空间 ,采用覆盖显示

#### 相对定位 / 绝对定位 / 固定定位 确定自身位置的方式:

这三种定位, 都是通过如下四种样式来完成位置确定的:

	1.	left:长度+单位;
	2.	top:长度+单位;
	3.	right:长度+单位;
	4.	bottom:长度+单位;

在相对定位中:
	表示元素相对与当前自身位置 , 进行指定方向的偏移.
	例如:	想让元素 向右移动10个像素:
			left:10px 或 right:-10px
	例如:	想让元素 向上移动10个像素
			bottom:10px 或 top:-10px;

在绝对定位中:
	默认情况下是: 距离body四个边框的距离
	存在相对/绝对/固定定位祖先元素时: 距离此祖先元素四个边框的距离.
	
	设置bottom:0px时, 不是距离body底边0px , 而是浏览器窗口;

在固定定位中:
	距离浏览器某个方向边界的 距离;

###CSS常用样式

####定位时的堆叠顺序 熟悉

	默认情况下, 元素编写越靠后, 显示时越靠前.
	
	设置堆叠优先级:
		z-index:数字值;
	
	作用:
		默认值为0 , 值越大, 越靠前. 负数表示显示在内容的后面.

####过渡 * 

	在元素的样式变更时 , 增加过渡时长, 让样式的更改更圆润.
	
	格式1:
		transition:样式名 时长s;
	格式2:
		transition:all 时长s;
	
	案例:
	
		.login_w{
			position: relative;
			left:200px;
			top:100px;
			width:300px;
			height:300px;
			background-color: #fff;
		}
		.qrcode{
			width:300px;
			position: absolute;
			left:75px;
			top:0px;
			transition:all 1s;
		}
		.hide{
			opacity: 0;
			transition:all 1s;
		}
		.hide:hover{
			opacity: 1;
		}
		.qrcode:hover{
			left:0px;
		}
	</style>
	</head>
	<body>
		<div class="login_w">
			<div class="qrcode">
				<img src="images/qrcode.png"><img class="hide" src="images/phone.png">
			</div>
		</div>
	</body>


###转换 熟悉

####2D转换

	transform:
		-	位置移动	:	translate(x,y);  
						x和y 表示横向和纵向的移动坐标.
		-	旋转	   	:	rotate(数字deg);
						数字值表示旋转的度数.
		-	缩放	 	:	scale(x,y);
						x和y 表示缩小和放大的倍数.
		-	翻转		:	skew(xdeg,ydeg);
						x和y 表示根据x轴和y轴翻转的度数

####3D旋转

	transform:
		-	x轴旋转:	rotateX(数字deg);
		-	y轴旋转: rotateY(数字deg);

###动画

指的是元素在多个样式之间 平稳的过渡.

格式:
	步骤1.	定义一个动画
			@keyframes 定义动画名称{
				0%{
					样式列表;
				}
				...
				100%{
					样式列表;
				}
			}
	步骤2.	使用这个动画
			选择器{
				animation:动画名称 执行时长s;
				animation-iteration-count:重复次数;
			}

