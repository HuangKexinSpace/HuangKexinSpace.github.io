---
title: Develop - Csharp & Unity 扫盲
date: 2024-10-11
description:
tags:
  - C#
---
Reference:  [Code monkey C# Beginner Tutorial](https://www.youtube.com/watch?v=pReR6Z9rK-o&t=88s)
# QAs with GPT
## Q1: 
这个c#脚本为啥没有实例化感觉就运行了？挂载到GameObject就是实例化了吗？向我解释C#的语法和逻辑。
## A1: 
在 Unity 中，C# 脚本的执行方式和一般的 C# 程序有所不同，这是因为 Unity 的运行环境和生命周期管理机制不一样。让我们详细看看为什么这个脚本在没有显式实例化的情况下依然可以运行，以及 Unity 的一些基础原理和 C# 的语法逻辑。
**Unity 中脚本的工作原理**
1. **挂载到 GameObject：**
• 在 Unity 中，当你将一个脚本挂载到一个 GameObject 上时，Unity 会自动管理这个脚本的生命周期。相当于在场景中存在的 GameObject 成为了这个脚本类的一个实例化对象。
• 只要场景中存在这个 GameObject，Unity 就会根据生命周期事件（如 Start、Update、OnDestroy 等）自动调用相应的方法。
2. **隐式实例化：**
• 当一个脚本被附加到一个 GameObject 时，Unity 实际上已经在内部为这个脚本类创建了一个实例，只是这个实例化过程是由 Unity 自动完成的，你不需要在代码中显式地调用 new 去创建对象。
• 所以你不需要像传统的 C# 程序那样使用 DoubleTabBackSceneCtrl myCtrl = new DoubleTabBackSceneCtrl();。Unity 在启动场景时会为你处理这些细节。
**C# 脚本在 Unity 中的生命周期方法**
Unity 使用 C# 脚本中的特殊方法来控制脚本的执行逻辑，这些方法根据特定的生命周期事件被自动调用：
1. Start() **方法：**
• Start() 是 Unity 中的一个生命周期方法，当脚本实例在场景中启用时调用一次。它通常用于初始化状态或绑定事件监听器。将事件监听器添加到 Start() 中，确保了它是在游戏对象被启用时就已经准备好响应事件了。
• 当脚本被加载到 GameObject 上并且对象启用后，Unity 自动调用这个方法。
2. Update() **方法：**
• Update() 是 Unity 中最常用的一个方法，它在每一帧都被调用，用于持续检查和更新游戏状态。
• 任何需要频繁更新的逻辑，如角色的移动、物理计算等，通常都在这个方法中实现。
3. OnDestroy() **方法：**
• OnDestroy() 是当对象即将被销毁时调用的方法，用于执行清理操作，如取消事件订阅、释放资源等。
**理解事件监听机制**
在你的代码中，SimpleTouch.Instance.OnDoubleTap.AddListener(OnDoubleTapCallBack); 的作用是为双击事件添加一个监听器。当事件被触发时，Unity 会自动调用你定义的 OnDoubleTapCallBack() 方法。这个事件监听机制与传统 C# 的事件机制类似，但由于 Unity 提供了一些特定的工具类和 API，使得这种操作更加简化和高效。
**总结**
在 Unity 中，脚本只需要挂载到 GameObject 上，就等于完成了实例化和初始化的过程。Unity 会管理脚本实例的生命周期，并自动调用这些生命周期方法，因此你不需要像传统 C# 那样显式地创建对象。所有这些都使得开发过程更加简单直观，同时也保持了灵活性。
## Q2:
public class SlamDemoCtrl : MonoBehaviour 这行：后面的是啥
## A2:
在这行代码中：
public class SlamDemoCtrl : MonoBehaviour
这里定义了一个名为 SlamDemoCtrl 的类，后面的 : MonoBehaviour 表示这个类继承自 MonoBehaviour。让我们详细解释一下：
	: MonoBehaviour：
	•	: 表示继承关系。在 C# 中，当一个类后面紧跟着一个冒号和另一个类的名字时，表示这个类继承了后面提到的类。
	•	MonoBehaviour 是 Unity 中的一个基础类，所有要附加到 GameObject 上的脚本类都应该继承自它。通过继承 MonoBehaviour，这个类就能够利用 Unity 特有的功能，如生命周期方法（Start()、Update() 等）和与 Unity 引擎的交互。
为什么继承 MonoBehaviour 很重要
继承 MonoBehaviour 是让一个类在 Unity 中能正常作为脚本组件使用的关键。只有继承了 MonoBehaviour 的类才能：
	•	被添加到 GameObject 作为组件。
	•	使用 Unity 提供的特殊方法，例如 Start()、Update()、OnDestroy()、Awake() 等生命周期方法。
	•	使用 Unity 提供的各种 API 和功能，例如协程（Coroutines）、物理操作、碰撞检测、脚本间通信等。
## Q3
我有一个Unity命名问题 为啥我在脚本中写的public GameObject m_PlaneDectection, 但是挂载在object面板上的名字就没有m_了呢？ 就只是PlaneDection？
## A3
在Unity中，变量名的显示方式在脚本和Inspector（检查器）面板中有所不同。即使在脚本中定义了带有前缀的变量名（比如 m_PlaneDetection），Unity 通常会在 Inspector 中自动移除这种前缀，以保持字段名更简洁和易读。
这是 Unity 的设计选择，目的是让 Inspector 中的变量更直观。Unity 会去掉常见的前缀（如 m_、_ 等），只保留主要的变量名。所以在 Inspector 中，你会看到变量名是 PlaneDetection，而不是带有前缀的形式。
如果你想在 Inspector 中显示带有前缀的变量名，可以使用 [SerializeField] 属性并手动重命名该字段。不过，这种做法一般不推荐，因为它会降低代码和 Inspector 的可读性。