---
title: "Create流程"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/xmasf32qhhasqxsa"
slug: "xmasf32qhhasqxsa"
doc_id: "189961468"
updated: "2024-10-22T14:45:01.000Z"
tags:
  - yuque
---

# Create流程

- StartHook

- 当我们通过按 N 打开 BuildWindow 时，会有一个BuildWindow创建 GUI 的逻辑。

- 首先BuildWindow继承了EntityCreateEditor，EntityCreateEditor 又继承了 EditorWindow，EntityCreateEditor 在OnGUI 中会创建许多 GUI 的 Button，所以BuildWindow 也继承了该功能。

- 当我们点击某个 Button 的时候，BuildWindow就会调用StartCreateController 方法，并传入实现了IBuildableDef接口的参数，也就说会传入具体需要创建的类型的，比如柱子。

- 之后逻辑就到PlayerController 中的StartBuildController了。

- 首先是在传入的 buildableDef不为空的情况下，停止所有的实体操作控制器。

- 然后由该buildableDef 去调用它的GetBuildController 方法，这个行为是多态的，不同的类型会去触发各自的GetBuildController 方法，返回值是实现了 IBuildController 的物体。

- 之后逻辑就到了ConstructionCreateController 类的Get泛型方法，上面的多态的影响到就是 Get 方法的泛型参数，比如柱子DownFencePillarDef 调用的就是ConstructionCreateController.Get<DownFencePillarBuildController>()，之后就会返回DownFencePillarBuildController。

- 现在逻辑又重新回到 PlayerController 了，刚刚得到的DownFencePillarBuildController 对象赋值给buildController_，之后执行 buildController_ .Start，并传入PlayerEntity.ins.city 和buildableDef。

- 首先DownFencePillarBuildController 继承DownFencePillarCreateController，DownFencePillarCreateController 又继承了ConstructionCreateController，ConstructionCreateController 实现了IBuildController 接口，该 Start 方法是由IBuildController 定义，在ConstructionCreateController 中实现，逻辑就是初始化 area 和constructionDef，并且开始 StartHook。

- StartHook 方法是由 DownFencePillarCreateController 实现的，因此由此执行。

- 如果在DownFencePillarCreateController 中 BaseDownFencePillarModel 这个类对象是空的， 那么 BaseConstructionModel 就会去调用CreateModel 方法，这个方法会在世界上创建一个空物体并给他添加对应的组件，比如 BaseDownFencePillarModel，并作为返回值返回该组件，然后赋值给DownFencePillarCreateController 中的 baseDownFencePillarModel_。

- 之后就将 downFencePillarDef 赋值给 baseDownFencePillarModel_ .downFencePillarDef，并且调用downFencePillarDef 的RefreshMaterial 方法和RefreshMesh 方法。

- 这两个方法都是调用的 DownFencePillarRenderer 下的RefreshMaterial 和RefreshMesh，然后将对应 Def 比如 DownFencePillarDef，赋值给meshRenderer.sharedMaterial 和meshFilter.sharedMesh。

- 逻辑又重新回到 PlayerController ，这个时候只剩把buildableDef 赋值给buildableDef_ 即可（目前该对象buildableDef还没有投入使用，后续想要获取当前正在建造的 Def 可以从此获取）。

- UpdateHook

-  在 PlayerController 中的 Update 中（由UpdateManager驱动），buildController_.Update()会不断被调用，也就是说ConstructionCreateController 中的 Update 会一直被调用。

- 那么ConstructionCreateController 中，UpdateHook 方法也会一直被调用。

- 那么实现了该UpdateHook 的类将会去不断调用对应逻辑，比如BeamCreateController。

- 首先会判断是否按下鼠标右键，如果按下，则将isSelectStartSlot_ 设为 false，并且关闭baseBeamModel_ 的 MonoBehaviour，然后重置鼠标光标，其实也就是把baseBeamModel_ 的startExpandUnit 和endExpandUnit 赋值为 0.
