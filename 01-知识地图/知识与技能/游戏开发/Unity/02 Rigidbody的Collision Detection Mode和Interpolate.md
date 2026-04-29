---
title: "Rigidbody的Collision Detection Mode和Interpolate"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/ih54ngaupw4xga9g"
slug: "ih54ngaupw4xga9g"
doc_id: "222955001"
updated: "2025-06-08T10:32:52.000Z"
tags:
  - yuque
---

# Rigidbody的Collision Detection Mode和Interpolate

#### 一、Rigidbody 碰撞检测模式（Collision Detection Mode）

- **Discrete（离散检测）**

- **作用**：默认模式，仅在每帧的固定时间步长（Fixed Timestep）检测碰撞。

- **特点**：性能最优（CPU开销约0.6ms/1000次碰撞），但高速物体可能穿透薄碰撞体（Tunneling）。

- **适用场景**：低速或静态物体（如NPC、平台、环境物体）。

- **Continuous（连续检测）**

- **作用**：检测物体运动路径上的碰撞，避免高速物体穿透静态碰撞体（如墙壁）。

- **特点**：仅对静态碰撞体启用连续检测，性能中等（约1.5ms/1000次碰撞）。

- **适用场景**：子弹、抛射物等高速物体撞击静态目标。

- **Continuous Dynamic（连续动态检测）**

- **作用**：对静态和动态刚体（设为Continuous/Dynamic）均启用连续检测。

- **特点**：精度最高，但性能开销最大（约1.7ms/1000次碰撞）。

- **适用场景**：高速物体撞击动态目标（如子弹打移动敌人）。

- **Continuous Speculative（推测式连续检测）**

- **作用**：通过预测性边界框计算碰撞，平衡精度与性能。

- **特点**：动态启用检测（移动时激活，静止时休眠），性能优于Continuous（约1.2ms/1000次碰撞）。

- **适用场景**：新项目默认选择，适合高速物体且需性能优化时。

#### 二、Rigidbody 插值模式（Interpolate）

用于平滑物体运动，解决因帧率波动导致的抖动问题。

- **None（无插值）**

- **作用**：直接使用物理引擎计算的原始位置和旋转，可能出现抖动。

- **适用场景**：高帧率稳定运行的环境（如PC端高配设备）。

- **Interpolate（内插值）**

- **作用**：基于前一帧的Transform平滑当前帧的运动，减少抖动。

- **特点**：运动更平滑，但会引入轻微延迟（滞后效应）。

- **适用场景**：摄像机跟随的玩家角色或需要平滑移动的物体。

- **Extrapolate（外插值）**

- **作用**：基于当前速度预测下一帧的位置，提前平滑运动。

- **特点**：响应更快，但高速运动时可能产生预测误差（抖动或 overshoot）。

- **适用场景**：需要快速响应的物体（如赛车、飞行器）。
