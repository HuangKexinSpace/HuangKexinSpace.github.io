---
title: RayNeoX2_02_Demo初探
date: 2024-10-09
description: 
tags:
  - AR
---
### Refer
- [官方文档](https://open.rayneo.cn/#/docs/x2?name=)
- [RayNeoX2_01_环境配置](https://huangkexinspace.github.io/posts/xr_rayneo/rayneox2_01_%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/)
# 构建第一个XR应用
- Follow： [官方文档](https://open.rayneo.cn/#/docs/x2?name=) - OpenXR Unity ARDK -最新 - 快速开始 - 构建第一个XR应用
## 添加XR Plugin 预制体
- 新建场景，最上方导航点Asstes - Create - Scene，新建的Scene（任何其他的东西）都会出现在Project的Assets文件夹中，然后我们把新建的这个New Scene拖到Hiearchy栏下。
- 在Unity中，Project下的Assets相当于仓库中的原料，把Assete中的东西从Project拖到Hierarchy上，就像是把原料摆到操作台上，而Scene/Game的视窗就是看看当前操作台上的东西长什么样子。
		![pic](../attachments/RayNeoX2_02_Demo初探.png)
		![pic](../attachments/RayNeoX2_02_Demo初探-1.png)
- 把New Scene中的Main Camera，Directional	light删除。
	![pic](../attachments/RayNeoX2_02_Demo初探-2.png)
	(然后就是一步一步跟着文档操作，我这里记录一些文档可能没有细节的步骤)
## 添加按钮和输入框
### 2. 配置Canvas
需要删除canvas下原有Graphic Raycaster,并添加我们的XRGraphicRaycaster
	![pic](../attachments/RayNeoX2_02_Demo初探-3.png)
	![pic](../attachments/RayNeoX2_02_Demo初探-4.png)

- 打包及投屏测试可以参考 [RayNeoX2_01_环境配置](https://huangkexinspace.github.io/posts/xr_rayneo/rayneox2_01_%E7%8E%AF%E5%A2%83%E9%85%8D%E7%BD%AE/)

	
	