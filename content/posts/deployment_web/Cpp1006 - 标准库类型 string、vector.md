---
title: 1005Cpp - 标准库类型string、vector
date: 2024-10-06
description:
tags:
  - Cpp
---
- **范围for循环**：处理字符串中的每个字符
```cpp
for (declaration:expression)
	statement
```
- 下标运算符：s[0] 代表第一个字符
## 3.3 标准库类型vector
From GPT：通俗地说，vector 是 C++ 中的**动态数组**，它可以自动调整大小，非常适合存储和管理一组数据。
- 加元素 push_back
- 若循环体内部包含有向vector对象添加元素的语句，则不能使用**范围for循环**。
## 3.4 迭代器
- v.begin()  表示v的第一个元素，若v为空，则它是尾元素的下一位元素。
- v.end() 表示v尾元素的下一位元素，即尾后迭代器。
- 迭代器类型：iterator 能读写元素 const_iterator 只能读不能写。
- begin 和 end 运算符：若对象是常量，begin和end返回const_iterator; 若不是常量，返回iterator。
- cbegin，cend 返回const_iterator。