---
title: "深入理解Unity中的FixedUpdate,FixedTimeStep和Maximum Allowed Timestep"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/lsaz2gqef9zclgbl"
slug: "lsaz2gqef9zclgbl"
doc_id: "222958241"
updated: "2025-06-08T12:08:16.000Z"
tags:
  - yuque
---

# 深入理解Unity中的FixedUpdate,FixedTimeStep和Maximum Allowed Timestep

原文链接：

[https://blog.lidia-martinez.com/fixedupdate-fixedtimestep-maximum-allowed-timestep-unity](https://blog.lidia-martinez.com/fixedupdate-fixedtimestep-maximum-allowed-timestep-unity)

中文解释版：

[https://juejin.cn/post/7008502979624091685](https://juejin.cn/post/7008502979624091685)

小感悟：

1、  其中一个小点可能会误解的就是，当前帧中物理模拟的执行时间也会被作为需要被模拟的时间计入进下一帧计算中。

举个简单的例子（游戏时间流逝和现实世界流逝比例相同的情况下），假设物理模拟耗时为 1ms，步长为 3ms，累计还需物理模拟的时长为 4ms，而一帧中渲染部分耗时也为 1ms。那么这一帧将会执行一次物理模拟，耗时 1ms，渲染帧耗时 1ms，模拟剩余时间为 1ms。这总和 3ms 将作为一个新的累计时间。下一帧执行的时候刚好凑满一次物理模拟，于是下一帧的执行为，1ms 物理模拟，1ms 渲染， 之前  剩余累计时间为 0ms，这总和是 2ms 为新的累计时间，而 2ms 不满足一次步长，于是，再下一帧将不会执行物理模拟，只有一次渲染耗时 1ms，于是累计时长变为 3ms，这样下下帧就刚好又可以执行一次物理模拟了。

通过以上的小例子也可以得知，正常情况下，游戏时间的滞后范围为 0-1 个步长之间。如果出现了超过最大步长的性能问题，则另算。

2、如果修改游戏流逝时间，其实就算修改了物理所需模拟的累计时间，流逝时间越快，累计的就越快，所需模拟的次数就会增加，那么性能消耗其实也就会越大。反制，流逝时间减慢，累计的时间就越慢，所需物理模拟的次数就会降低，性能可能会有所缓和，但这也意味着物理精度降低，可能会出现闪现等特殊问题。
