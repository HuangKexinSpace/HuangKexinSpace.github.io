---
title: 【1004更新】python基础语法
date: 2024-10-04
description:
tags:
  - python
---
- 切片
```python
# step是步长 左闭右开
list[start:end:step] 
```
- for i in range (a,b) 左闭右开
- 升序排列函数
	- sorted(list, reverse = True)
- 取最小值
```python
list = [1,2,3]
min(1,2,3)
min(list)
```
- 装饰器 和 静态方法
	在 Python 中，@ 符号用于装饰器（decorators）。装饰器是一种特殊的函数，允许你在不改变原始函数代码的情况下，为函数、方法或类添加额外的功能。
	@staticmethod 是 Python 中内置的一个装饰器，它表明该方法是一个静态方法（static method）。静态方法与普通方法不同，它不依赖于类的实例来调用。换句话说，静态方法不需要访问类的实例或类的属性，而是直接通过类本身调用。
	静态方法常用于工具类（如 JSONUtils），当你需要将某些功能与类进行逻辑上的关联，但又不需要访问实例属性时，可以使用静态方法。
- 生成n✖️n的二维矩阵：matrix = [[0] * n for _ in range(n)]