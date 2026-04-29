---
title: "PlayerEntity"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/mr5gnki34k3nar8y"
slug: "mr5gnki34k3nar8y"
doc_id: "189951875"
updated: "2024-10-12T08:06:47.000Z"
tags:
  - yuque
---

# PlayerEntity

- PlayerEntity 继承了HumanEntity 和各种修饰接口。

- 声明了一个IActionSys 接口，用于规范带有行为的系统。

- 定义一个自身静态的成员变量，用于作为单例，保证全局唯一和方便调用。

- 组合一个 PlayerDef，用于提供预定义的数据。

- 组合了许多系统，我们真正的逻辑处理都是由各个系统去执行相应逻辑。在 PlayerEntity 中的系统，需要实现接口的用类来定义，不需要实现接口的使用结构体来定义。但为什么这么设计呢？

-
