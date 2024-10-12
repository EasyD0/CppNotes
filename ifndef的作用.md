---
创建时间: 2024-04-15, 13:09:11
更新时间: 2024-04-15, 13:12:24
---
在头文件中常常可以看到
```cpp
#ifndef xxx
#define xxx

//代码正文
```
这到底起了什么作用?

当第一次遇到该文件时, xxx 没有被定义过, 那么将执行下面的内容
- 定义 xxx
- 准备编译代码正文
第二次遇到该文件时, xxx 已经被定义过了, 后面的所有内容都会跳过, 包括

xxx 一般为文件名的大写, 不同的头文件中 xxx 一般不同.
但在实验中, 可以举特殊例子, 在两个头文件中 xxx 都相同, 测试它的作用


```cpp
//myhead1.h
#ifndef MYHEAD_H
#define MYHEAD_H

int fun1(){return 1;}

//myhead2.h
#ifndef MYHEAD_H
#define MYHEAD_H

int fun2(){return 2;}

//main.cpp
#include "myhead1.h"
#include "myhead2.h"
int main(){
	fun1();
	fun2();
}
```