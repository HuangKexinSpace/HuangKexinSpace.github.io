---
title: Develop - Cpp - const限定符号、处理类型
date: 2024-10-04
description:
tags:
  - Cpp
---
# Cpp
## 2.4 const限定符
### 指针和const
```cpp
int errNumb = 0;
int *const cuErr = &errNumb; //cuErr是一个指向int型对象的常量指针 它只指errNumb 不准变
const double pi = 3.14;
const double *const pip = &pi;// pip是一个指向常量对象的常量指针
```
- 指针本身是一个常量并不意味着不能通过指针修改其所指对象的值，需要看指向的对象是否可变。
### 顶层const
- 顶层const表示该对象本身是常量，底层const表示指针和引用所指的对象是常量。
### constexpr和常量表达式
```cpp
const int sz = get_size(); //sz不是常量表达式
```
尽管sz本身是一个常量，但它的具体值直到运行时才能获取，所以也不是常量表达式。
- 声明为**constexpr**的变量一定是一个常量，而且必须用**常量表达式**初始化，初始化了就不准变了，也不准重新赋值。
## 2.5 处理类型
### 类型别名 
```cpp
//两种起别名的方式
typedef double wages;
using SI = Sales_item;
```
- 指针、常量和类型别名
	不能直接替换来理解，而是要把别名的东西和修饰整体理解。这里有些抽象，遇到具体的再补充。
### auto类型说明符
- auto定义的变量必须要有初始值
- 复合类型、常量和auto
	auto一般回忽略顶层const，保留底层const
### decltype类型指示符
- decltype的作用是选择并返回操作数的数据类型：
```cpp
decltype(f())sum = x; //sum的类型就是函数f的返回类型
```
## 2.6 自定义数据结构
