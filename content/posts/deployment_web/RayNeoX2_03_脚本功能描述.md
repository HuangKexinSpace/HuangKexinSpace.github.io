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
```c#
using RayNeo.API;
using UnityEngine;

public class SlamDemoCtrl : MonoBehaviour
{
    public GameObject m_Cube;
    public int m_LineCount = 10;
    public float m_CubeSpace = 0.3f;
    // Start is called before the first frame update
    void Start()
    {
    //开启slam
        Algorithm.EnableSlamHeadTracker();
    //创建cubes
        CreateCubes();
    }
    private void OnDestroy()
    {
    //关闭slam
        Algorithm.DisableSlamHeadTracker();
    }
    //动态创建满屏的cube
    private void CreateCubes()
    {
//中心点为长度的一半
        int centerPoint = m_LineCount / 2;
	
        for (int i = 0; i < m_LineCount; i++)
        {
            for (int j = 0; j < m_LineCount; j++)
            {
            //Instantiate是Unity中用来创建对象的方法
                var c = Instantiate(m_Cube);
			//设置空间位置
                c.transform.position = new Vector3(m_CubeSpace * (i - centerPoint), m_Cube.transform.position.y, (m_CubeSpace * (j - centerPoint)));

            }
        }
    }
    // Update is called once per frame
    void Update()
    {
    }
}

```
# FacialRecog 内置脚本描述

