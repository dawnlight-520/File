## Node.js

#### 一. Linux 上安装 Node.js

##### 		1. 直接使用已编译好的包

​		Node 官网已经把 linux 下载版本更改为已编译好的版本了，我们可以直接下载解压后使用：

```
# wget https://nodejs.org/dist/v10.9.0/node-v10.9.0-linux-x64.tar.xz    // 下载
# tar xf  node-v10.9.0-linux-x64.tar.xz       // 解压
# cd node-v10.9.0-linux-x64/                  // 进入解压目录
# ./bin/node -v                               // 执行node命令 查看版本
v10.9.0
```

解压文件的 bin 目录底下包含了 node、npm 等命令，我们可以使用 ln 命令来设置软连接：

```
ln -s /usr/software/nodejs/bin/npm   /usr/local/bin/ 
ln -s /usr/software/nodejs/bin/node   /usr/local/bin/
```

##### 		2. Ubuntu 源码安装 Node.js

以下部分我们将介绍在 Ubuntu Linux 下使用源码安装 Node.js 。 其他的 Linux 系统，如 Centos 等类似如下安装步骤。

在 Github 上获取 Node.js 源码：



```
$ sudo git clone https://github.com/nodejs/node.git
Cloning into 'node'...
```

修改目录权限：

```
$ sudo chmod -R 755 node
```

使用 **./configure** 创建编译文件，并按照：

```
$ cd node
$ sudo ./configure
$ sudo make
$ sudo make install
```

查看 node 版本：

```
$ node --version
v0.10.25
```

##### 3. Ubuntu apt-get命令安装

命令格式如下：

```
sudo apt-get install nodejs
sudo apt-get install npm
```

##### 4. 安装错误时：

```
# apt-get remove nodejs   //删除nodejs  
# sudo apt install curl
# curl -sL https://deb.nodesource.com/setup_8.x | sudo bash -     //nodejs源  
# apt-get update //更新包  
# sudo apt-get install nodejs //安装nodejs  
# sudo npm install npm -g //更新npm  
```

#### 二. 第一个Node.js程序：Hello World！

##### 1. 脚本模式

以下是我们的第一个Node.js程序：

实例

```
console.log("Hello World");
```

保存该文件，文件名为 helloworld.js， 并通过 node命令来执行：

```
node helloworld.js
```

程序执行后，正常的话，就会在终端输出 Hello World。

##### 2. 交互模式

打开终端，键入node进入命令交互模式，可以输入一条代码语句后立即执行并显示结果，例如：

```
$ node
> console.log('Hello World!');
Hello World!
```

#### 三.  Node.js 应用组成：

1. 引入 required 模块：**我们可以使用 **require** 指令来载入 Node.js 模块。

2. 创建服务器：**服务器可以监听客户端的请求，类似于 Apache 、Nginx 等 HTTP 服务器。

3. 接收请求与响应请求** 服务器很容易创建，客户端可以使用浏览器或终端发送 HTTP 请求，服务器接收请求后返回响应数据。

#### 四. Node.js 函数

在JavaScript中，一个函数可以作为另一个函数的参数。我们可以先定义一个函数，然后传递，也可以在传递参数的地方直接定义函数。

Node.js中函数的使用与Javascript类似，举例来说，你可以这样做： 

```
function say(word) {
  console.log(word);
}

function execute(someFunction, value) {
  someFunction(value);
}

execute(say, "Hello");
```

 以上代码中，我们把 say 函数作为execute函数的第一个变量进行了传递。这里传递的不是 say 的返回值，而是 say 本身！ 

 这样一来， say 就变成了execute 中的本地变量 someFunction ，execute可以通过调用 someFunction() （带括号的形式）来使用 say 函数。 

 当然，因为 say 有一个变量， execute 在调用 someFunction 时可以传递这样一个变量。 

#### 五. 案例练习

##### 1：各种图形打印案例

菱形、空心菱形

```
var a='';
for(i=0;i<6;i++){
    for(j=6;j>i;j--){
        a+=' ';
    }
    for(k=0;k<2*i+1;k++){
        a+='*';
    }
    a+='\n';
}
for(i=5;i>0;i--){
    for(j=7;j>i;j--){
        a+=' ';
    }
    for(k=0;k<2*i-1;k++){
        a+='*';
    }
    a+='\n';

}
console.log(a);

var a='';
for(i=0;i<6;i++){ 
    for(j=6;j>i;j--){
        a+=' ';
    }
    for(k=1;k<=2*i-1;k++){
        if(k==1||k==2*i-1){
            a+='*';
        }else{
            a+=' ';
        }
        }
        a+='\n';
}
for(i=4;i>0;i--){
    for(j=5;j>=i;j--){
        a+=' ';
    }
    for(k=1;k<=2*i-1;k++){
        if(k==1||k==2*i-1){
            a+='*';
        }else{
            a+=' '
        }
    }
    a+='\n';
}
console.log(a);
```

回字型：

```
var a ='';
for(i=0;i<7;i++){

    for(j=0;j<7;j++){
        if(i==0||i==6){
            a+='* ';
        }else{
            if(j==0||j==6){
                a+='* ';
            }else{
                if((2==i||i==4)&&(j>=2&&j<=4)){
                        a+='* ';
                }else if(i==3&&j==3){
                                a+='  ';
                }else if(i==4&&(j==2||j==4)){
                        a+='* ';
                }else if(i==3&&(j==2||j==4)){
                                a+='* ';
                }else{
                        a+='  ';
                }

            }
        }
    }
    a+='\n';
}
    console.log(a);

```

梯形、空心梯形：

```
var a='';
for(i=1;i<6;i++){
    for(j=0;j<2*i+1;j++){
        a+='*';
    }
    for(k=5;k>2*i+1;k--){
        a+=' '
    }
    a+='\n';
}
console.log(a);

var a='';
for(i=1;i<6;i++){
    for(j=0;j<=2*i+1;j++){
        if(j==0||j==2*i+1){
            a+='*';
        }else if(i==5){
            a+='*';
        }else if(i==1){
            a+='*';
        }else{
            a+=' ';
        }
    }
    for(k=5;k>2*i+1;k--){
        a+=' '
    }
    a+='\n';
}
console.log(a);
```

##### 2： for循环、if判断操作字符串

获取字符串长度

```
function xlen(str){
                        var len = 0;
                        var arr = new Array();
                        var txt = '';
                        while(undefined != str[len]){

                                len++;
                        }


                        console.log(len);
                }
                xlen('abasdasdcd');

```

拆分字符串

```
function xsplit(str,s){
                        var len = 0;
                        var arr = new Array();
                        var txt = '';
                        var flag = true;
                        var a = 0;
                        while(flag){
                            if(str[len]==s){
                                arr[a]=txt;
                                txt='';
                                a++;
                            }else if(undefined != str[len]){
                                txt += str[len];
                            }
                            if(undefined == str[len]){
                                arr[a] = txt;
                                console.log(arr);
                                flag=false;
                            }
                            len++;
                        }
                }
                xsplit('a,b,c,d',',');

```

合并字符串

```
function xprint(str,s){
                        var len = 0;
                        var arr = new Array();
                        var txt = '';
                        var flag = true;
                        var a = 0;
                        var b = 0;
                        while(flag){
                            if(str[len]==s){
                                arr[a]=txt;
                                txt='';
                                a++;
                                b++;

            }else if(undefined != str[len]){
                                txt += str[len];
                            }
                            if(undefined == str[len]){
                                arr[a] = txt;
                                console.log(arr);
                                flag=false;
                                b++;
                            }
                        len++;
                        }
                        var zf = '';
                        for(i=0;i<len-b;i++){
                            zf += arr[i];
                        }

                        console.log(zf);
                }

                xprint('a,b,c,d',',');

```

查询字符串

```
function xfind(zf){
                        var len = 0;
                        var arr = new Array();
                        var txt = '';
                        var flag = true;
                        var a = 0;
                        var b = 0;
                        var str = 'a,b,c,d,e';
                        var s = ',';
                        while(flag){
                            if(str[len]==s){
                                arr[a]=txt;
                                txt='';
                                a++;
                                b++;
                            }else if(undefined != str[len]){
                                txt += str[len];
                            }
                            if(undefined == str[len]){
                                arr[a] = txt;
                                flag=false;
                                b++;
                            }
                            len++;
                        }
                        indexof = function(zf){
                            for(var i = 0; i < len-b; i++){
                                if(zf==arr[i]){
                                    return i;

                                }else if(i==len-b-1){
                                    return -1;
                                }
                            }

                        }
                        console.log(indexof(zf));


                } 

                xfind('d');

```

截取字符串

```
function xcut(s1,s2){
                        var len = 0;
                        var arr = new Array();
                        var txt = '';
                        var flag = true;
                        var a = 0;
                        var b = 0;
                        var str = 'a,b,c,d,e,f,g,h,q,w,r,t,y,u';
                        var s = ',';
                        while(flag){
                            if(str[len]==s){
                                arr[a]=txt;
                                txt='';
                                a++;
                                b++;
                            }else if(undefined != str[len]){
                                txt += str[len];
                            }
                            if(undefined == str[len]){
                                arr[a] = txt;
                                flag=false;
                                b++;
                            }
                            len++;
                        }
                        var zf = '';
                        cut = function(s1,s2){
                            if(s1>=0 && s2<len-b){
                            for(i = s1;i<=s2;i++){
                               zf += arr[i];
                            }

                              return zf;
                            }
                         }
                        console.log(cut(1,3));


                }

                xcut(1,3);

```





















































