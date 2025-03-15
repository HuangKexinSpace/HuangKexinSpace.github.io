---
title: Develop - Cpp - 标准库类型string
date: 2024-10-05
description:
tags:
  - Cpp
---
# 3.2 标准库类型string
- 读写string 对象
	- 在进行读取cin操作时，string对象会自动忽略开头的空白（空格、换行 制表），从第一个真正的字符读起，直到遇到下一个空白停止。cin不进空格的。
	- 保留空白符号：用getline。
```cpp
//输入1，遇到空白停止
string in1;
cin>>in1;
cout<<in1<<endl;
//输入2，遇到空白换行输出
string in2;
while(cin>>in2)
	cout<<in2<<endl;
//输入3，原样输出空白符
string in3;
while(getline(cin,in3))
	cout<<in3<<endl;
```