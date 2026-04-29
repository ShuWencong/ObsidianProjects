---
title: "GameManager"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/cuzngfughgfe562x"
slug: "cuzngfughgfe562x"
doc_id: "189946212"
updated: "2024-10-12T07:29:09.000Z"
tags:
  - yuque
---

# GameManager

- 初始化整个游戏世界 TempGamePlayer   ------->   GameManager

						NewPresetGame 传入 cityID

- GameManager 开始调用所有需要初始化的 Manager。

- 基本上需要预设资源的 Manager 初始化的逻辑都是一致的，不过有些细节上不一致。

-  一部分通过 AssetManager 的泛型 GetAll 方法得到对应 List，那么我们可以遍历这个 List，然后存入到对应的字典中。另外一部分则多一步，通过AssetManager 的 GetAll 方法得到的是 TextAsset，这个时候我们在遍历的时候，就需要通过 JsonManager 的泛型Deserialize 方法把文本格式转化为我们想要的数据，再存入字典中。前者是 ScriptObject 类型，后者是 Json 格式的文本。
