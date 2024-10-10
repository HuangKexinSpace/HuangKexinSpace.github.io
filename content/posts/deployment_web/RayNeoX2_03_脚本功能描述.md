---
title: RayNeoX2_03_脚本功能描述
date: 2024-10-10
description: 
tags:
  - AR
---
## 内置脚本描述
### double Tab Back Scene Ctrl
```c#
using UnityEngine;
using UnityEngine.InputSystem;
using UnityEngine.SceneManagement;

public class DoubleTabBackSceneCtrl : MonoBehaviour
{
//双击方法
    public void OnDoubleTapCallBack()
    {
        SceneManager.LoadScene("Entry");
    }
    void Start()
    {
        SimpleTouch.Instance.OnDoubleTap.AddListener(OnDoubleTapCallBack);
    }
    private void OnDestroy()
    {
        if (SimpleTouch.SingletonExist)
        {
            SimpleTouch.Instance.OnDoubleTap.RemoveListener(OnDoubleTapCallBack);
        } 
    }
}
```
功能：双击返回“Entry”场景
用法：挂载到空的GameObject上