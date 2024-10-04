---
title: mac配置conda环境
date: 2024-10-04
description:
tags:
  - other
---
conda：类似于pip的包管理器，用于创建和管理虚拟环境，因为不同项目所需的包的版本不同，虚拟环境可以很好地区分和管理这些不同的包，类似于给每个项目划分出一个小房间，每个小房间可以放不同的工具。
### conda 和venv的比较
• venv：Python 自带的轻量级虚拟环境管理工具。它只处理 Python 解释器及其依赖库，不支持管理其他语言或工具。venv 从 Python 3.3 开始内置，适合于单纯的 Python 项目。

• conda：一个更强大的包管理和环境管理工具，适用于多个编程语言（不仅限于 Python），可以管理 Python 版本、依赖库、其他编程语言（如 R）、以及外部工具（如 MKL、HDF5）。它不仅支持 Python，还支持其他科学计算库和工具，常见于 Anaconda 或 Miniconda 发行版。

### 环境配置
reference：[YoutubeTutorial](https://www.youtube.com/watch?v=drbaFALFKDg)
- 在[官网](https://www.anaconda.com/)上freedownload mac版本，一路向前安装到底。
- 然后在终端用conda指令创建环境
### conda 指令

创建：conda create —name xxx python=…
删除：conda remove -n EnvName - -all
进入：conda activate EnvName
退出：conda deactivate