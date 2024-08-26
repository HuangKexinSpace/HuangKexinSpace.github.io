---
title: 为网站获取https协议
date: 2024-08-26
description: 
tags:
  - other
---

前言：买域名+解析+ssl证书部署+买服务器都是在腾讯云完成的。
### 购置域名

域名购买网址：https://buy.cloud.tencent.com/domain
### 域名解析

1. 腾讯云控制台-我的域名：[我的域名](https://console.cloud.tencent.com/domain/all-domain/all)在域名栏的DNS状态，点击管理解析。或者也可以直接在腾讯云搜索DNS解析。
	![pic](../attachments/为网站获取https协议.png)

2. 第一步点击后跳转到域名解析页面：https://console.cloud.tencent.com/cns/detail/teachernonverbal.asia/records
    1. 点击快速添加解析，如果有服务器的话就填主机IP，想要把网站部署到第三方托管平台的话，就点域名映射。如果在腾讯云买了服务器的话点腾讯云资源解析。还没想好/还没买好服务器的话就先点邮箱解析。
    2. 点确定后，大约过几分钟域名就会解析好。
	    ![pic](../attachments/为网站获取https协议-1.png)

### ssl证书签发下载

1. 在腾讯云搜索框搜索SSL，跳转到网址：https://console.cloud.tencent.com/ssl
2. 点我的证书，然后点申请免费证书，根据指示填写。
	![pic](../attachments/为网站获取https协议-2.png)
	![pic](../attachments/为网站获取https协议-3.png)
3. 填写完成几分钟后，站内信会提示SSL证书审核通过。这个时候回到我的证书页面，点击下载，选择Nginx。会下载下来一个压缩包，先放好。
	![pic](../attachments/为网站获取https协议-4.png)
	![pic](../attachments/为网站获取https协议-5.png)
### 服务器租赁

1. 我选择了腾讯云的轻量应用服务器（便宜，需求不大），在腾讯云买服务器的网站上选轻量云服务器：[https://cloud.tencent.com/product/lighthouse](https://cloud.tencent.com/product/lighthouse)
    
2. **选择应用模板的时候要选这个宝塔Linux面板，这个很大程度上会方便部署****SSL****证书。**
	![pic](../attachments/为网站获取https协议-6.png)
3. 后续操作：租赁好服务器后，在控制台中进入服务器页面，然后点域名解析。添加需要的域名。
	![pic](../attachments/为网站获取https协议-7.png)