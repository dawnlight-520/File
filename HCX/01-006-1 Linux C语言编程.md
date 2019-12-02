# 006  Linux C语言编程

## 第1章  重识C语言

* #### C语言概念---摘自维基百科

  C语言是一种通用的.过程式的编程语言

  ANSI C 美国规定的C语言唯一算法,作为C语言的标准.

* C语言的特点

  1. 简单
  2. 快速
  3. 高性能
  4. 兼容性好
  5. 功能强大
  6. 易于学习

* C语言的用途

  1. Linux嵌入式	------小工具-->linux系统,unix系统,操作系统

  2. 和硬件打交道的程序:ARM嵌入式/单片机编程/Arduino,

     可以直接和内存打交道,因此可以用来做硬件编程.

  3. 有性能要求较高的应用程序:一种著名服务器NGINX性能 = Apache *10倍以上

     ​													       									C语言   =    C++

     

## 第2章  C语言开发环境与配置

### vim常用命令

```
sudo apt-get update   ---更新最新资源地址

sudo apt-get install + 要安装软件名   ---安装某个软件

cd 目录名    ---切换目录

cd ~   ---进入到当前目录的home家目录

pwd   显示当前目录位置

ls   列出当前目录下的所有子目录和文件

ls -l   ---显示当前文件类型/创建日期/以及用户权限/用户主目录

clear  清除屏幕

touch 文件名   ---创建新的空文件

mkdir   创建新目录

rm文件名   ---删除文件

vi/vim 文件名    ----创建新文件并打开

:q 退出
 :w 保存
 :wq 保存退出

默认为命令模式，按ESC从其他模式返回命令模式。

命令模式下输入命令先按“：”再加上命令

切换模式不需要按“：”，直接输入命令。

#### （1）插入
i：进入插入模式，在当前光标前插入字符
a：进入插入模式，在当前光标后插入字符
o：进入插入模式，从下一行开始插入字符
shift+i：进入插入模式，在当前光标的行首插入（shift表示大写）
shift+a：进入插入模式，在当前光标的行尾插入
shift+o：进入插入模式，在当前光标上一行插入

#### （2）删除
x   ---删除光标处的字符
dd   ---删除整行
```



## 第3章  C语言常用命令&第一个C程序

cc/gcc -v   ---安装gcc运行环境

cc-v  检查cc编译器版本信息 

```
#include <stdio.h>

    int main() {  
    printf("hello world!\n");
 }
```

* 备注:

  \#include<stdio.h>导入标准输入输出流

  在Linux中不要使用void main，要使用有返回值的

  缩进4个空格

  保存并退出  :wq  

  编译:  cc 文件名.c

  执行:  ./文件名.out

  r 可读 

   w 可写

   x 可执行

  

## 第4章 C语言多文件操作

### 第1节  多个源文件分而治之

- [ ] 最大值max

  #max.c

```
#include <studio.h>

int max (int a, int b){
    if(a>b){
        return a;
    }else{
        return b;
    }
}

int main(){
    int a1=33;
    int a2=21;  
    int maxNum=max(a1,a2);
    printf("the max value is %d",maxNum);
    return 0;
}
```

- [ ] 最小值min

  #min.c

```
int min (int a, int b){
    if(a<b){
        return a;
    }else{
        return b;
    }   
}

int main(){
    int a1=33;
    int a2=21;  
    int minNum=min(a1,a2);
    printf("the min value is %d",minNum);
    return 0;
}
```

* #### 分文件

vim可以同时打开多个文件：

在命令模式下输入“：”:sp xx.xx 新建一个文件（如：:sp max.c），

分屏: Ctrl+W+下箭头  切换到下边的代码文件

​           Ctrl+W+上箭头   切换到上边的代码文件

打开显示行号 “ :set nu ”

将代码复制粘贴到其他文件 按“ p ”

把打开的文件同时保存并退出“  :wqa ”



<>在系统库里查找

""在当前的目录查找

cd ~/workspace/

返回命令模式 esc

剪切本行以及下面的若干行  数字+dd

把打开的文件同时保存并退出  :wqa

编译两个文件 gcc max.c hello.c -o main.out

写一个输出数据名称 -o main.out

###  第2节  头文件与函数定义分离

- [ ] #max.c

  ```
  #include <stdio.h>
  
  int max (int a, int b){
      if(a>b){
          return a;
      }else{
          return b;
      }   
  }
  ```

  #max.h

  ```
  int max(int a,int b);
  ```

- [ ] #min.c

  ```
  int min (int a, int b){
      if(a<b){
          return a;
      }else{
          return b;
      }   
  }
  ```

  #min.h

  ```
  int min(int a,int b);
  ```

- [ ] #hello.c

  ```
  #include <stdio.h>
  //#include "max.c"
  #include "max.h"
  #include "min.h"
  
  int main (){
      int a1=33;
      int a2=21;
      int maxNum=max(a1,a2);
      int minNum=min(a1,a2);
      printf("the max value is %d \n,the min value is %d \n",maxNum,minNum);
      return 0;
  }
  ```

gcc - c max.c -o max.o

//#include<stdio.h>

gcc max.o hello.c

编译之后生成 .o文件



拷贝文件  cp 

把不常改动的函数，类和框架提前编译好生成静态库

查看源代码 cat hello.c

.o文件不可读

.h文件放声明  int max(int a,int b);

#include"max.h" 便于让没有编写max函数的人使用max函数

gcc max.o min.o hello.c 3个文件一起写入，否则找不到max，min函数



c语言的入口文件是main 函数

：sp max.c 新建了一个max.c,光标在上面

ctrl+w+/downarrow 光标跳转到下面

:set nu 显示行数

：9(行数字)+dd 剪切复制这几行代码到剪切板

:ctrl+w+/uparrow 

gcc -c max.c -o max.o 编译成机器码



cc -c a.c -o a.o

将c文件转换成二进制文件

cc a.o main.c

a.h 自创头文件



分开编译：gcc -c 文件名.c -o 文件名.o

编译成文件名.o后，需修改主函数文件，注意原文件.c的声明

然后在编译主程序时：gcc 文件名.o 文件名.c————节省时间，加快速度

拷贝文件：cp 文件名.c（复制文件） 文件名.c（粘贴文件）

把不常修改的程序编译后保存为“静态库”，方便使用，加快编译速度。

查看源代码程序：cat 文件名.c

使用别人的静态库.o文件可以创建.h文件，然后在源程序中#include<文件名.h>来引用



\#include "文件名.c"相当于复制进项目,但执行较慢 

gcc -c 文件名.c -o 文件名.o //编译文件提高调取速度 

gcc 文件名.o 文件名1.c //编译执行文件（gcc后要把关联的o文件都加入） 

模仿stdio.h，我们生成 文件名.h（包含.o文件所含的函数声明；这个分号一定不能少）#include "文件名.h" 告诉协作人员函数的类型 

cp 文件 文件2 //拷贝文件并命名为文件2 

cat 文件名 //查看文件内容

总结：对于不经常修改的类库和框架，提前编译成静态库



# 第5章 makeFile工具的编写

删除多文件   rm * + 文件后缀名（如：rm * .o）

make把大型的开发项目分成若干个易于管理的模块,可以很清晰和很快捷到整理源文件

检查make是否存在   make  -v

安装make工具   sudo apt-get install make

创建并编写make文件   vi Makefile

约定Makefile 文件   #this is make file

注释声明   #include "filename"（其中\#include 表示预处理指令）

hello.out:max.o min.o hello.c   //max.o和min.o hello.c一起生成hello.out文件

​    gcc max.o min.o hello.c(8个空格或代表8个空格的tab键)

max.o:max.c

​    gcc -c max.c

min.o:min.c

​    gcc -c min.c

执行make

hello.out:max.o min.o hello.c -o hello.out



# 第6章 main函数详解

### 第1节  main函数中的return

主函数的正确的行为：int main（int argv，char* argc[]）

gcc main.c-o main.out && ./main.out两条语句一起执行,前一个命令执行成功之后才会执行后一个命令

判断是否执行成功：  echo $?  若执行成功则返回“0”

例如：./main.out && ls

只有当返回值为0时，才会执行ls命令进行查看目录

故main函数中的“return 0”为判断main函数执行成功的返回值

return 0;

### 第2节  main函数中的参数

* #### argv参数

  ```
  #include<stdio.h>
  
  int main(int argv,char* argc[ ]){
      printf("argv is %d\n",argv); 
      int i;
      for(i=0; i<argv; i++){
          printf("argc[%d] is\n", i, argc[i]); 
       }
       return 0;
  }
  ```

  main函数的完整形式：int main(int argv,char* argc[])

  C语言程序在Linux运行的时候，可以跟操作系统进行交互，可以完美兼容

  将两个命令一起执行：命令一 && 命令二（带命令一成功执行后进行命令2）

  程序执行后判断程序是否正常执行：echo $?-----返回0为正常----所以main函数中return必须为0，才能让系统判断为正常执行

  main 函数中 argv参数 表示执行该程序时 输入的有效项（程序名+参数）个数； 

  ​               		 argc参数 表示执行该程序时输入的有效项内容（程序名， 参数）；

  main 中 argv 和 argc 的作用:   

  ​			 argv 表示参数的个数;  

   			argc 存放参数的内容;

  

# 第7章  C语言中输入输出流和错误流

### 第1节  标准输入流输出流以及错误流

stdin 标准输入流 键盘

stdout标准输出流 显示器

stderr标准错误流

printf是对fprintf的封装

fprintf(stdout,  );

scanf是对fscanf的封装

fscanf(stdin,"%d",&a);

fprintf(stderr," ");

标准输入stdin 重定向机制

重定向到该文件，无覆盖

重定向到该文件，最新

<重定向输入文件

1>正确结果导入 2>错误结果导入应用程序将数据从stdin文件中读取出来，输入到应用程序。缺省情况下，从键盘读取 。 

标准输出 stdout 应用程序将产生的数据写入stdout文件。缺省情况下，应用程序将 stdout 输出到屏幕上。 

标准错误 stderr是程序写入其错误消息的位置。只有应用程序执行错误，返回值不是0时，才写入 stderr文件， 默认将stderr显示在屏幕上。 

fscanf(stdin(或文件名),"%d",&a);//从文件读取数据 

fprintf(stdout(或文件名),"%d",a);//将数据写入文件

fprintf(stderr, %d",a);//将数据写入stdrr标出错误流

### 第2节  输入流输出流以及错误流的重定向

* #### linux 通道

  由于linux是面向全世界开源，所以就要有一种机制确保不同应用程序之间协调使用。		------  重定向机制

* #### 重定向机制

  标准输入流		--->		键盘输入

  标准输出流		-->		终端输出

  标准错误流		-->		错误输出

  重定向机制

  \>>重定向到该文件，无覆盖

  \>重定向到该文件，最新

  <重定向输入文件

  1>正确结果导入 2>错误结果导入

  ./a.out执行a.out

  ./a,out 1>>a.txt输出流重定向，a.out输出内容到a.txt，在a.txt原有的内容上增加，1可有可无

  ./a,out >a.txt输出流重定向，a.out输出内容到a.txt，覆盖a.txt原有内容

  cat a.txt 打开a.txt文件并输出

  ls /etc >>etc.txt把etc的内容添加到etc.txt中

  ./a,out <a.txt输入流重定向，a.txt输入内容到a.out

  rm *.txt删除所有的txt文件

  ./a.out 1>t.txt 2>f.txt <input.txt标准输出流，标准错误流，标准输入流

  

# 第8章  管道原理及应用

管道：|

查看根目录： ls /

查看Linux默认配置目录： ls /etc/

将etc文件输出到一个管道：ls /etc/ | grep 关键字符

（如：ls /etc/ | grep ab：要查找某个目录下有多少个文件名包含"ab"）

“|”是文件输出到grep，作为grep的输入，在Linux中作为管道，用于连接在两个独立的小程序建立通道，比如将“ls”的输出结果传给“grep”的输入

grep是C语言的小程序，可以查询包含指定字符的文件

查看当前进程的文件：ps（查看进程的命令） -e

（如：ps -e | grep ssh  查看目前有多少含有ssh的进程应用）



# 第9章  打造实用C语言小程序

输入输出流的指定并不是在程序中直接写出。程序中还是以标准输入流输出流（prinf（）输出到屏幕 scanf（）由屏幕输入）写。写完之后，执行时，重新指定。      

重定向：

​           1..重定向到某个文件。用>>或>

​            2.作为其他程序输入流。使用管道  |

```
int flag=1; 
while(flag){
   scanf("%d",&i);
   if(i==0)break;//结束循环，如果没有这一步就一直在输入,造成死循环所以当输入为0的时候,结束循环,即结束输入 
}
例如：1
  			 2
			 3
			 4
			 0//这时结束循环  
```

#### 【编写使用管道的程序】

 我们在文件夹下，c语言做的每个程序都有一个独立的功能，我们可以将多个小程序使用管道连接到一起。

```
我们现在写一个程序avg.c，求任意个数的平均值：
#include <stdio.h>

int main(){
    int s,n;
    scanf("%d\n,%d\n",&s,&n);
    float v = s/n;
    printf("v=%f\n",v);
    return 0;
}
退出vim进行编译cc avg.c -o avg.out，我们得到avg.out，我们输入3000，3;最后输入0，结束程序，输出平均值。
```

```
我们再写一个统计输入的程序input.c：
#include <stdio.h>

int main(){
    int flag = 1;
    int i;
    int count = 0;
    int s = 0;
    while(flag){
        scanf("%d",&i);
        if(0 == i) break;
        count ++;
        s += i;
    }
    printf("%d,%d\n",s,count);
    return 0;
}
我们对这个函数进行编译cc input.c -o input.out，我们输入3000 2000 0，输出总工资5000和人数2。
```

我们不妨使用以上两个程序结合起来，将所有数据进行统计input.out，之后通过管道经过avg.out计算平均值，命令可以写为./input.out | ./avg.out，然后进行输入，输入完成我们便得到了对应的平均工资。 

以上就是通过管道，将两个小程序连接起来得到更复杂的程序的过程