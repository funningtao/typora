# CMake

https://www.cnblogs.com/ph829/p/4759124.html

https://blog.csdn.net/bytxl/article/details/50635016

https://www.cnblogs.com/xianghang123/p/3556425.html

https://blog.csdn.net/wzzfeitian/article/details/40963457/

基本上是下面这一套总结

https://blog.csdn.net/ajianyingxiaoqinghan/article/details/70230902

[CMake常用语法](https://www.jianshu.com/p/8909efe13308)

## 前言

1、每一个需要进行cmake操作的目录下面，都必须存在文件CMakeLists.txt 。
2、cmake指令不区分大小写。本文为了醒目，笔者把cmake指令都作大写处理。
3、变量使用${}方式取值，但是在 IF 控制语句中是直接使用变量名；
4、指令(参数 1 参数 2…)，参数使用括弧括起，参数之间使用空格或分号分开

## helloworld

**目录结构**

`hello/
|– CMakeLists.txt
|– build /
|– main.c`

```makefile
#cmake最低版本需求，不加入此行会受到警告信息
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

#项目名称
PROJECT(HELLO) 

#把当前目录(.)下所有源代码文件和头文件加入变量SRC_LIST
AUX_SOURCE_DIRECTORY(. SRC_LIST)

#生成应用程序 hello
ADD_EXECUTABLE(hello ${SRC_LIST})
```

`step2/
|-- mian.cpp
|-- src
	|-- Test1.h
	|-- Test1.cpp`

​	

```makefile
PROJECT(main)
CMAKE_MINIMUM_REQUIRED(VERSION 2.6) 

#指明项目包含一个src子目录
ADD_SUBDIRECTORY( src )
AUX_SOURCE_DIRECTORY(. DIR_SRCS)
ADD_EXECUTABLE(main ${DIR_SRCS}  )

#可执行文件mian需要连接一个名为Test的链接库
TARGET_LINK_LIBRARIES( main Test )
```

在子目录中的CMakelist.txt

```makefile
AUX_SOURCE_DIRECTORY(. DIR_TEST1_SRCS)
ADD_LIBRARY ( Test ${DIR_TEST1_SRCS})
```

####