##  条件编译指令

```c
#ifndef __HEADERNAME_H__
#define __HEADERNAME_H__
/*声明、定义语句*/
#endif
```

防止头文件被重复引用

要确保宏名唯一性

命名格式

>  \<PROJECT>\_\<PATH>\_\<FILE>\_H_ 
>
> 项目名称
>
> 头文件相对路径
>
> 文件名
>
> \_H_

 #pragma once方式来防止头文件被重复引用 

### 使用条件编译指令实现源码的部分编译

1.#if指令

该指令检测表达式值是否为真。如果表达式的值为真，则编译后面的代码直到出现 #else、#elif 或 #endif 为止，否则不编译。

2.#endif指令

该指令用于终止 #if 指令。

3.#else指令

该指令用于 #if 指令之后，当前面的 #if 指令的条件不为真时，就编译 #else 后面的代码。

4.#elif指令

该指令综合了 #else 和 #if 指令的作用。下面的示例代码演示了 #if、#else、#elif 与 #endif 的组合使用情况

```c
#if OS==1
    printf("V1.0");
#elif OS==2
    printf("V2.0");
#else
    printf("未知");
#endif
```

5.#ifdef和#ifndef

相对于 #if 指令（检测表达式的值是否为真），#ifdef 和 #ifndef 指令用于检测指令关键字后面的宏名称是否已经定义。其中，#ifdef 指令表示如果宏已经被定义，那么它的检测结果为真，否则返回假；而 #ifndef 指令的含义正好与 #ifdef 指令相反，它表示如果宏未被定义，那么它的检测结果为真，否则为假 