---
title: RayNeoX2_03_脚本功能描述-Slam
date: 2024-10-10
description: 
tags:
  - AR
---
# Slam Demo 内置脚本描述
## GameObject
### double Tab Back Scene Ctrl
```c#
using UnityEngine;
using UnityEngine.InputSystem;
using UnityEngine.SceneManagement;

public class DoubleTabBackSceneCtrl : MonoBehaviour
{
//构造了一个方法，双击就退出到“Entry”场景
    public void OnDoubleTapCallBack()
    {
    //加载”Entry“场景
        SceneManager.LoadScene("Entry");
    }
    void Start()
    {
    //这句是为双击添加监听器，当触发双击后执行OnDoubleCallBAck这个函数
        SimpleTouch.Instance.OnDoubleTap.AddListener(OnDoubleTapCallBack);
    }
    private void OnDestroy()
    {
    //移除监视器的常规操作
        if (SimpleTouch.SingletonExist)
        {
            SimpleTouch.Instance.OnDoubleTap.RemoveListener(OnDoubleTapCallBack);
        } 
    }
}
```
功能：双击返回“Entry”场景
用法：挂载到空的GameObject上
## SlamDemoCtrl
- 空Object 位置000
### Slam Demo Ctrl
![pic](../attachments/RayNeoX2_03_脚本功能描述.png)
