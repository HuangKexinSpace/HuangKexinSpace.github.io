---
title: Notes for Writing Prompt
date: 2024-10-24
description:
tags:
  - llm
---
Reference: [我是如何赢得GPT-4提示工程大赛冠军的](https://mp.weixin.qq.com/s/J8J_8ht7NSgbpJV5HNyhgA): 
1. 使用CO-STAR框架搭建Prompt解构
	- context：与任务有关的背景信息
	- objective：LLM需要执行到任务
	- style：写作风格
	- tone：语气
	- audience：目标受众
	- response：响应的格式，理想格式应该是json
2. 使用分隔符，例如### content ### or <<< content >>>