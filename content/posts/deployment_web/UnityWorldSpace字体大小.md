---
title: Unity - World Space下设置UI中到字体大小
date: 2025-04-14
description:World space下UI的字体大小与DPPU和front szie有关，Screen space下与RPPU有关。 
tags:
  - AR
---
# 疑问🤔
- Unity中，为什么canvas（world space）下的text，需要在Canvas scaler的范围内，调整Dynamic pixels Per Unit 到一定数值，才可以调整front size大小，否则调front size大小没有用？
- 其中dynamic pixels per unit（DPPU） 和 reference pixels per unit（RPPU） 分别有什么作用和关系，我需要大致设置什么数值，有什么规律？

# Q & A
- 在 World Space 模式下，Canvas 的 UI 元素（例如 Text）可能会出现你“调整 font size 没有效果”的情况，原因往往是 Canvas Scaler 中的设置未配合好，特别是 Dynamic Pixels Per Unit (DPPU) 的数值。

## Dynamic Pixels Per Unit 是什么？
- Dynamic Pixels Per Unit (DPPU)：控制 UI 元素的像素密度（即1单位世界空间 = 多少像素），它影响的是字体的实际视觉大小。
- 举例：如果设置为10，意味着1单位世界空间的长度对应10像素；如果设置为 100，对应的视觉细节就会更小。
✅ **在 World Space Canvas 中，DPPU 是字体显示效果的核心控制参数！**

##  Reference Pixels Per Unit 是什么？
- Reference Pixels Per Unit (RPPU)：这是 基于 Canvas Scaler 的缩放参考值，控制 UI 在不同屏幕分辨率下的缩放行为。
- 主要作用在于 屏幕空间（Screen Space）Canvas，对于 World Space 的影响较小。
  
##  为什么调整 font size 没效果？
在 World Space Canvas 中：
	1.	font size 设置的是字体的像素大小；
	2.	但这些像素被 DPPU“缩放”后，才映射到世界单位上；
	3.	如果 DPPU **设置太大**，比如10000，就算你 font size 设置为 100，也只是 100 / 10000 = 0.01 单位，几乎看不见；
	4.	所以你会觉得 font size 没有效果，其实是 DPPU 把它“压扁”了。

## World Space下 推荐DPPU在10-100之间，DPPU = 100 即1m=100px

