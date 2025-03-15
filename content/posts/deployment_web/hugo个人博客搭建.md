---
title: Develop - hugo个人博客搭建（for mac）
date: 2025-03-16
description: 重新记录📝了一下hugo的部署过程
tags:
  - web
---

# 依赖项安装

- Git

- Go: https://go.dev/doc/install

  - Check if sucessful installed

    ```
    go version
    ```

- Dart Sass: brew install sass/sass/sass

  - Check if sucessful installed

    ```
    hugo env
    ```

---

## 安装Hugo for mac

- 安装命令

  ```
  brew install hugo
  ```

- check命令

  ```
  hugo version
  ```

## 新建网站

- 安装一个主题的minimal command

```
hugo new site quickstart
cd quickstart
git init
git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
echo "theme = 'ananke'" >> hugo.toml
hugo server
```

### 一步一步安装

- 在终端的自定义存放hugo的文件夹下运行

  ```
  hugo new site your_folder_name
  cd your_folder_name
  git inti
  git submodule add your_choosed_theme_github_url
  echo "theme" = 'theme_name'">>hugo.toml
  ```

- 启动hugo查看网站

  ```
  hugo server
  # 启动hugo查看保存的草稿但未发布指令
  hugo server -D
  ```

- 添加内容

  ```
  hugo new content content/posts/post_title.md
  ```

- 发布网站

  ```
  hugo
  ```

###  在Github托管Hugo

- Create a Github repository（个人仓库，仓库名为账号名），注意⚠️不要添加readme.md
- git remote add origin url
  - Check: git remote -v

- Follow the step3-10: https://gohugo.io/host-and-deploy/host-on-github-pages/

# 日常编辑
- 配置页面: 根目录下hugo.toml文件
## 内容更新
- 新建posts
  - createfile: 根目录/content/posts/new_yourpostname.md
  - fileconfig:
  ```
  ---
    title: Develop - Cpp - 复合数据类型、const限定符
    date: 2024-10-03
    description:
    tags:
    - Cpp
  --- 
  ```
- 为your_post插入图片
  - 在posts目录下新建一个放置图片的文件夹
  - 在your_post中输入如下markdown指令
    ```
    ![pic](../picturefilename/picturename.png)
    ```
  - 创建带caption的图片
    ```
    {{< figure src="../picturefilename/picturename.png" title="figurecaption" width="80%" >}}
    ```
# Github自动部署后的push命令
```
git add .
git commit -m "update_info"
git push origin
```
