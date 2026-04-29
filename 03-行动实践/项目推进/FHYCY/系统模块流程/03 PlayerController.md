---
title: "PlayerController"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/ildduke0z3kypiml"
slug: "ildduke0z3kypiml"
doc_id: "189792617"
updated: "2024-12-22T16:01:52.000Z"
tags:
  - yuque
---

# PlayerController

在 PlayerController 的 Update 中持续调用几个重要的方法MoveUpdate，ActionUpdate，UIUPdate、UseUpdate 等

- MoveUpdate

- MoveUpdate 中首先是监听玩家的Horizontal 和Vertical 输入。

- 通过监听Horizontal 和Vertical 输入，转化为枚举类型的EDirection2D8X，其中的值有八个方向，为了让人物的移动要随着摄像机方向移动，我们可以通过摄像机的四种枚举EDirection2DCorner，将方向对应矫正，返回的值仍然是EDirection2D8X 的，这个枚举的值是基于世界的 ，而不是自身的。

- 将得到的枚举值归一化，转化为单位向量后赋给 inputDirection，之后需要使用方向时，直接使用该值。

- 在正式移动之前，会有许多的条件判断，例如跳出水缸，有没有切换一些移动姿态等，如果有，那么直接执行对应的逻辑，而不是正常移动。

- 判断了一些前置条件后，需要先调用一个onStartMove 委托，

- 如果前面的条件都不满足，最后就到了正常移动。

- 需要判断当前是在骑马还是在步行，对应的状态（疾跑或慢走）是怎么样的，然后执行对应的移动。

所以，当我们需要扩展移动相关的逻辑时，可以加在MoveUpdate 中，当我们需要作为一个特定状态下的移动时，可以加在正式移动模块之前，而当我们存在其他移动模式或状态时，可以加在正常移动模块。

- ActionUpdate

- 按照顺序不断监听玩家 KeyConfig 中的交互按键

- 先判断当前是否处在一些特殊状态，比如骑马，驾驶战车，经营饭店等，如果在那么会判断当前是否处于能够脱离的状态，如果也满足，就会在 KeyTips 中将对应的可执行事件显示出来，如果跟随指示，触发了对应按键，那么玩家将执行对应方法。

- 之后判断一些鼠标与物品的逻辑，当鼠标指向某个可交互物品时，会通过GetTrigger获取对应的IEntityLink，然后获取其中的 entity， 之后比对前置条件是否满足，比如（Interactive.mouseHoverEntity is HandSwitchEntity handSwitchEntity），满足则显示对应指示按钮（部分不显示）。

- 监听玩家的下一步指示，比如左键，右键，中键等，然后去执行对应逻辑，每个逻辑由对应 System 处理。

所以，当我们需要扩展行为相关逻辑时，可以加在 ActionUpdate 中，然后依次判断当前是否满足拥有对应组件，当前是否按下对应交互按键，再调用 Entity 的对应 System 的方法。

- UIUpdate

- 如果 MoveUpdate 中有监听到Horizontal 或 Vertical ，那么isFrameMove_ 就会变成 true，那么这个时候UIManager 会关闭掉所有 npc 交互面板。

- 触发对应的道具交互按钮之后，会调用 ItemSystem，并将对应的索引传入，去调用对应栏位的道具。

- 手持不同道具，会对状态机造成影响，因此也需要调用对应的 PlayerMode 去执行道具对应动作。

- 最后刷新 UI 对应的显示效果。

- UseUpdate

- 当正在执行 Use 行为时，会去接着不断调用对应useState_ 下的使用行为，如放置，投掷等，

- 若不处于 Use 行为下，即为EUseState.Null 时，则会根据useEntity 判断其属于哪个实现类，然后执行对应的逻辑。

- 执行逻辑时，可能有两个条件需要判断，一是isHit，二是can。

- isHit 就是根据鼠标的屏幕位置，让摄像机发送一条射线，碰撞到了对应的 Layer 后，即满足 isHit。

- can 则是判断当前的状态下或当前距离下是否能够执行该 Use 行为。

- 前置条件都满足后，就执行对应的使用逻辑即可。

所以，当我们需要扩展使用相关逻辑时，可以加在 UseUpdate 中，根据需求，添加前置条件以及对应的使用逻辑。
