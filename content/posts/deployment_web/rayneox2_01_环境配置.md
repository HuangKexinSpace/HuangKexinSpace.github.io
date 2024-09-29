---
title: rayneox2_01_环境配置
date: 2024-09-27
description:
tags:
  - AR
---
- [官方文档](https://open.rayneo.cn/#/docs/x2?name=)
- [开发手册](https://leiniao-ibg.feishu.cn/wiki/OwFfwCpgqiEekBkSRwlcJuRPnoc)：
### 环境配置
- 参考教程： [官方文档](https://open.rayneo.cn/#/docs/x2?name=) - OpenXR Unity ARDK - 最新 -  快速开始 - 开发环境搭建
	（上述文档写的比较清晰，可以一步一步按照上述文档配，下面是我的配置记录）
1. 安装Unity版本，安装时勾选 andriod build support，如果没勾选也可以安装后在设置的add mdules里再安装。 **（推荐22.3.42f1或者2022.3.44f1 ，其他好几个版本都报错了）** 
	![pic](../attachments/RayNeoX2_01_环境配置-1.png)
	![pic](../attachments/RayNeoX2_01_环境配置.png)
2. 创建3d core template
	![pic](../attachments/RayNeoX2_01_环境配置-2.png)
3. 导入雷鸟sdk - 我选择安装包导入，也可以根据文档的从git中导入。
	[安装包链接](https://leiniao-ibg.feishu.cn/drive/folder/PrgcfKIiPlxamJdkdRScLaI2nod)（第二个）
	![pic](../attachments/RayNeoX2_01_环境配置-6.png)
	![pic](../attachments/RayNeoX2_01_环境配置-3.png)
	![pic](../attachments/RayNeoX2_01_环境配置-4.png)
	![pic](../attachments/RayNeoX2_01_环境配置-5.png)
4. 导入成功后会提示重启，自动重启后如果控制台报错，再关掉unity再重启，如果还报错，大概率可能会是unity版本不兼容.....如果不报错，就继续🏃‍♀️
5. 设置打包到安卓平台 
	![pic](../attachments/RayNeoX2_01_环境配置-7.png)
	点switch platform
	![pic](../attachments/RayNeoX2_01_环境配置-8.png)
6. 环境配置 edit - project setting
	![pic](../attachments/RayNeoX2_01_环境配置-9.png)
	Player - other settings identification 勾选 重写包名
	![pic](../attachments/RayNeoX2_01_环境配置-10.png)
	XR Plug- in Management - 安卓平台下 勾选OpenXR和RayNeo XR feature group 然后点击红色感叹号。
	![pic](../attachments/RayNeoX2_01_环境配置-12.png)
	点击fix all
	![pic](../attachments/RayNeoX2_01_环境配置-13.png)
	Open XR - RayNeo Support 的设置 - 关掉ATW support
	![pic](../attachments/RayNeoX2_01_环境配置-14.png)
7. **其他设置**（必须）
	Project setting - player - publish setting -build -勾选custom main manifest
	![pic](../attachments/RayNeoX2_01_环境配置-15.png)
	随后可在Unity>Project>Plugin>Android 文件夹下，找到自动生成的AndroidManifest.xml，将该文件的代码替换成：
	![pic](../attachments/RayNeoX2_01_环境配置-16.png)
```
<?xml version="1.0" encoding="utf-8"?>

<manifest

xmlns:android="http://schemas.android.com/apk/res/android"

package="com.unity3d.player"

xmlns:tools="http://schemas.android.com/tools">

<application>

<activity android:name="com.rayneo.openxradapter.UnityOpenXrActivity"

android:theme="@style/UnityThemeSelector">

<intent-filter>

<action android:name="android.intent.action.MAIN" />

<category android:name="android.intent.category.LAUNCHER" />

</intent-filter>

<meta-data android:name="unityplayer.UnityActivity" android:value="true" />

</activity>

<meta-data android:name="com.rayneo.mercury.app" android:value="true" />

</application>

</manifest>
```
### 将 Sample build 到眼镜中
1. 导入sample，windows - package manager - Rayneo Openxr ardk - Samples - import
	![pic](../attachments/RayNeoX2_01_环境配置-17.png)
2. File - Build settings， 然后在Porject栏 Samples - RayNeo OpenXR ARDK - Scenes 下面根目录加上两个文件夹中的场景全部拖到Build Settings 页面中的Scenes in Build中。然后点Build。
	![pic](../attachments/RayNeoX2_01_环境配置-19.png)
	
 * 注意build这一步可能会有很多报错，可能遇到的情况：
 1. 提示选了两个输入方式，只能有一个，根据他的提示关掉一个。
 2. 安卓platform版本不够，根据他的提示选择升级版本 这里建议平台升级成34。
 3. 操作后如果还是报错 清除缓存（mac的在Unity - setting-GI cache里，win的话网上搜一下），重启再build一下。
 4. （这个对我很有用！！）可能的解决方法：https://discussions.unity.com/t/failed-to-update-android-sdk-package-list-error-when-using-sdk-installed-with-unity/753351/14

