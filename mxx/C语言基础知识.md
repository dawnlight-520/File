### C语言基础知识

#### 一：简介

##### 1 标准语法：ANSI C

##### 2 特点：

简单/快速/高性能/兼容性好/功能强大/易于学习

##### 3 适合

​	linux嵌入式：1 小巧灵活

​								2 语法简单

​								3 适合做小工具

​	和硬件打交道的程序：系统

​	有高性能要求的应用程序，如nginx服务器

​	ARM嵌入式/单片机/Arduino/   

#### 二：语言环境

##### 1 linux系统内

​	ubnutu

windos/苹果系统内，安装虚拟机，在虚拟机上安装linux系统

##### 2 常用指令：

​		更新本地资源    sudo apt-get update

​		安装软件             sudo apt-get install 软件名称

​		clear 清屏

#### 三：代码编写

创建xx.c文件，进入编辑模式，写入代码：vi xx.c

		> #include <stdio.h>  //屏幕的输出流
		>
		> int main（）			//main方法及返回值类型
		>
		> {
		>
		> ​	printf("hello world!\n");   //打印hello world！
		>
		> ​    return 0;
		>
		> }

执行代码：cc xx.c  完成编译  //xx.out

​						./xx.out  完成输出 // hello world!

#### 四：基本原理编写

##### 1 基本写法：

%d   表示打印的是十进制整型数据的实际长度

%s   表示的是打印一个字符串

```
#include <stdio.h>

#include "max.c"

int max(int a, int b)
{
        if(a>b){
                return a;
        }else{
                return b;
        }
}

int main()
{
        int a1=3;
        int a2=2;
        int maxNum=max(a1,a2);
        printf("the max value is %d",maxNum);
        return 0;
}
```

##### 2 写法优化：

#####   //新的命令：

 gcc -c max.c -o max.o

编译max.c文件，输出max.o文件

---

#include <stdio.h>
#include "max.h"

#include "min.h"

int main()
{
        int a1=3;
        int a2=2;
        int maxNum=max(a1,a2);
        int minNUM=min(a1,a2);
        printf("the max value is %d\n,the min value us %d\n",maxNum,minNUM);
        return 0;
}

---

int max(int a, int b);

---

int min(int a, int b);

#### 五  makeFile的编写

make -v    查看make版本号

rm *.o   删除所有的.o 文件

#开头为注释

文件名：Makefile

> #this is make file

> hello.out:max.o min.o b.c
>        	 gcc max.o min.o b.c -o hello.o  //依赖关系时用Tab来缩进8个空格
> max.o:max.c                     / /依赖关系
>       	  gcc -c max.c
> min.o:min.c                      //依赖关系
>         	gcc -c min.c

#### 六   main函数中的return

##### 1 原本写法：

> #include <stdio.h>

> int main(int argv,char* argc[])
> {
>         printf("hello world!\n");
>         return 0;
> }

gcc main.c -o main.out && ./main.out  //可同时执行编译及输出

echo $?    //结果：0       说明运行到了return 0；最后一步没出错

//在&&符号前返回值为0时，会继续执行后面的程序

##### 2  main函数中的参数

> #include <stdio.h>

> int main(int argv,char* argc[])
> {
>         printf("argv is %d \n",argv);
>         return 0;
> }

//gcc main2.c -o main2.out && ./main2.out       //argv is 1   

argv 表示执行了几条命令

argc[ %d ]  is %s   表示第%d个命令执行的是%s命令  

> #include <stdio.h>

> int main(int argv,char* argc[])
> {
>         printf("argv is %d \n",argv);
>
> ​		int i;
>
> ​		for(i=0;i<argv;i++){
>
> ​			printf("argc[%d] is %s\n",i,argc[i]);
>
> ​		}
>
> ​        return 0;
> }

输出结果：

//    argv is 1 
//argc[0] is ./aa.out

#### 七  标准输入/输出流  错误流

##### 1  代码演示  

> #include <stdio.h>
>
> /*
>
> stdin    输入流
>
> stdout  输出流
>
> stderr   错误流
>
> */
>
> int main()
> {
>         printf("hello world\n");
>         int a;
>         scanf("%d",&a);
>         printf("input value is :%d\n",a);
>         return 0;
> }

//hello world
//./aa.out
//input value is :32764

> #include <stdio.h>

> int main()
> {
>        // printf("plase input the value a :\n");
>
> ​		fprintf(stdout,"plase input the value a :\n");   //标准输出流
>
> ​        int a;
> ​       // scanf("%d",&a);
>
> ​		fscanf(stdin,"%d",&a);							//标准输入流

			>if(a<0){
			>
			>​		fprintf(stderr,"the value must > 0\n");   //标准错误流
			>
			>}

> ​      //  printf("input value is :%d\n",a);
> ​        return 0;
> }

##### 2  重定向

​       cat 文件名   //查看该文件信息

​		重定向机制：

​		标准输出流重定向：用   >>   表示定向位置指向，表示把结果追加到结尾

​									            用    >   表示定向位置指向，表示把结果覆盖更新

 		标准输入流重定向：用   <<  表示定向位置指向，表示把结果追加到结尾

​									            用    <   表示定向位置指向，表示把结果覆盖更新

#### 八  管道原理

​		命令示例： ls /etc/ | grep ab    //grep  查询包含指定字符的行

​																	//查询etc文件中包含ab的所有文件

​		|  表示管道，从文件etc输出查询结果(输出流)，并输入grep文件中（输入流）

​		ps -e | grep ssh //查看linux系统的ssh进程是否启动

#### 九 实用小程序

利用管道可以将多个小工具拼凑到一起使用，实现功能强化；

平均值算法：

##### 1：avg.c

		#include <stdio.h>
		int main()
		{
	        int s,n;
	        scanf("%d,%d",&s,&n);//s表示所有数之和，n表示有几个数
	        float v=s/n;
	        printf("v=%f\n",v);
	        return 0;
		}

##### 2：input.c

```
#include <stdio.h>

int main()
{
        int flag=1;
        int i;
        int count=0;
        int s=0;
        while(flag){
                scanf("%d",&i);
                if(0==i) break;
                count++;
                s+=i;
        }
        printf("%d,%d\n",s,count);
        return 0;
}

```



##### 利用管道运行1 /  2：

​      ./input.out | ./avg.out     //可直接得到平均数值



















​	