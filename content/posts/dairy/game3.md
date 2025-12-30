---
title: 游戏开发日记（3）- 251227
date: 2025-12-26
description: Done&Todo/美术风格参考/mj学习笔记/垫图指令
tags:
  - game develop
---

# Done
- 学了下midjourney的使用，设定了人物立绘的关键词，根据两种风格（像素风、某插画风）生成了几张人物立绘，还算不错，感觉可以直接用了。尝试了垫图，效果也还不错。大概最多生成3-5种风格就需要选定一种了，不过目前对这个插画风生的图非常满意hhh。

# TODO
- 序章详细文本
- 序章开发
- 序章美术素材生成


# 美术风格参考
## 像素风
{{< figure src="../attachments/25122701.png" title="像素风-潜水员戴夫" width="80%" >}}
- pixel art
- 8-bit game

## 插画风1
{{< figure src="../attachments/25122702.png" title="小红书某插画风（用这个风格生成了超满意的立绘，很大概率游戏美术就是这个风格了）" width="80%" >}}

🪄Prompt解析：
风格词：扁平插画、扁平人物
艺术风格：极简艺术、卡通、高饱和度
画面描述:看着镜头、近距离头像
后缀：--ar 3:4 --style expressive --s 750
	
🔮完整咒语：
Girl avatar, cute avatar, short hair, white hair, flat illustrations, flat characters, cartoon, looking at the camera, holding a cat in hand, close-up avatar, minimalist art, high saturation, yellow blue background, solid color background


# Midjourney学习笔记
## 一般prompt词写法思路
1) Prompt 的固定骨架
把一条 prompt 分成 6 块，顺序也基本固定：
	1.	主体是谁（Subject）：角色类型/身份
	2.	不可妥协的特征（Must-have）：发型、年龄感、体型比例、标志物
	3.	服装/道具（Outfit/Props）：材质、层次、关键物件
	4.	画面表达（Presentation）：游戏立绘/角色卡/正侧背三视图、姿势、构图
	5.	风格与美术规则（Style Bible）：你游戏的统一风格词（固定一套）
	6.	环境与光色（Scene/Lighting/Palette）：可固定也可按章节变
固定的通常是：
	•	角色身份+世界观关键词（赛博/奇幻/校园…）
	•	角色“辨识度”特征（发型长度、脸型、标记、主色、道具）
	•	你的统一风格词（例如：2D low poly、flat shading、clean shapes、limited palette）
	•	输出形式（立绘/角色卡/三视图/头像）
每次你描述的（变量）通常是：
	•	当张的动作、情绪、镜头距离
	•	当张的服装版本（冬装/战斗装/休闲装）
	•	当张背景（空白/场景/渐变色）
	•	当张光照氛围（清晨/霓虹/逆光）
⸻
1) 参数（旋钮）里哪些算“固定”，哪些算“调参”
	•	--ar 画幅（立绘常用 --ar 2:3 或 --ar 9:16，头像 --ar 1:1）
	•	--v 版本（当前默认v7）。--niji 6 偏二次元
	•	--seed 种子（锁定seed之后，改细节就是微调特征了）
用于探索的旋钮：
	•	--s / --stylize：越高越“艺术化自由发挥”，越低越“听话执行”
	•	--chaos：越高越发散出奇招，越低越稳定可控
	•	--no：负面约束（比如 --no short hair）
  - --sref 图片的url 风格参考
  - --sw 风格强度 0-1000
版本不同可用参数细节会有差异，但“固定画幅/版本/seed + 调 stylize/chaos/–no”这个训练方法基本通用。
⸻
1) 一条“骨架模板”
模板：
[角色身份与世界观], [不可妥协特征清单], [服装道具], [姿势表情], [呈现方式], [固定风格词], [光色/背景] --ar X:Y --v ? --s ? --chaos ? --seed ? --no ?




