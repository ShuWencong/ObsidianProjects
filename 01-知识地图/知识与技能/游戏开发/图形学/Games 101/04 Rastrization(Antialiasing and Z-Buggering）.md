---
title: "Rastrization(Antialiasing and Z-Buggering）"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/huh8zx6cai2g2i31"
slug: "huh8zx6cai2g2i31"
doc_id: "197455799"
updated: "2024-12-05T19:03:54.000Z"
tags:
  - yuque
---

# Rastrization(Antialiasing and Z-Buggering）

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416806721-6c9f142c-af0a-4b82-88b5-523e53bc2a84.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416857525-c56bb271-261e-4784-8d81-f2ddc6053879.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416876664-28759e43-bf57-41fa-be87-d61cc58847cc.png)

采样带来的问题，锯齿

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416900982-5cdcd0ac-9fc0-4581-af4a-46a21affac77.png)

采样带来的问题，摩尔纹

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416998101-a9751a10-6da4-4160-9905-5a28045751f1.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733417233573-3c682ec9-6071-47b1-95eb-20e87f7f14cc.png)

直接采样得到的结果是走样的

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733417253599-c05802e4-b698-4761-93a2-c2ca70cc3a58.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733417320662-30be730b-b8d9-4ead-a6ff-a3bf58ec43a7.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733417407924-ab18dde1-2425-4df1-aad8-59d87998f7df.png)

傅里叶变换，它可以把一个函数转化为不同频率的段，并且显示出来

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733417504324-2372eba4-00ab-4eda-b759-efe678b1d6f4.png)

傅里叶变换是可逆的

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733417516366-476513d3-a23f-44eb-8694-d5c338289d65.png)

采样频率不够导致取出来的函数恢复后，是明显走样的。

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733417722775-931184ef-22d7-4b27-a707-7e83a3b46195.png)

两个完全不同频率的函数，采样出来的却是一样的结果，导致无法区分，这就是走样！

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733417798433-65530669-2ba9-40e0-95cb-85581826a2a3.png)

滤波，去掉一些频率的段

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733417858246-a71df203-7903-4696-bec1-fe8959860bd6.png)

我们认为一个信号是重复的，那么这个图在水平和垂直上都存在无限多个，因为图片左右边界和上下边界是衔接不上颜色的，所以右边会出现一个十字，因为图片边界发生了突变。

傅里叶变换让我们看见图形在各个频率长什么样。可视化看见任何信号在不同频率下的样子，也叫做频谱。

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733417964081-82350b8f-69a5-4a01-afcb-e3e4b736406f.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733418801822-5dcabb68-1902-4660-95e9-274cf449aa3f.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733418672772-0afa28a0-cd5c-41b4-9bda-210548c61929.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733418870190-dec4f68b-b2d6-455b-aa0e-310433968d20.png)

卷积示例

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733418944718-4f1f3818-4bc9-41c6-b4b6-43c878631af3.png)

对一个图片进行卷积有两个方法，直接对实域卷积，或者对频域叉积

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733419269900-684c0246-1978-400a-8eaa-b2da7a41bc6a.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733419548814-d6b58cd1-04c6-4328-8782-f57ef7f24de7.png)

卷积盒就是将图片的像素值通过求平均达到模糊边界的效果。

卷积盒越大，边界就会越模糊，但同时整体也会变得模糊。

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733419574455-2a25f8cb-8b39-4514-adc9-23716a14a4ec.png)

卷积盒的实域越大，对应的频域越小。

可以通过极限举例，当卷积盒无限小的时候，其他图片通过该卷积盒后，几乎所有像素值都不变，那么这个卷积盒反应在频域上就是非常大的，因为几乎所有的值都通过了该卷积盒的滤波。

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733419688778-fa5f5180-d2bb-4525-bafe-d6716163ff73.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733419700339-408de444-af93-4c04-b166-5262317744cc.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733420358679-d98e9261-3218-4d7c-a3ba-10b333374fae.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733420738826-4630ccaf-c585-486b-acb0-c39a42fffd6d.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733421341259-616ef80f-70c3-4628-accb-653447137c6d.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733421533488-68e6b0fb-e880-4fc4-b6ae-84af12090311.png)

先模糊再采样，减少混叠情况。

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733421680978-e431f654-3e67-4977-ac19-4f9f23cd1d47.png)

先模糊再采样，得到的像素值是正确的，那么我们要考虑，这个模糊操作具体应该如何进行？

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733421771192-9bd36f72-d8cc-47a7-9718-21078f9adeb7.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733422387088-8576f2ab-dcaa-4c9d-884e-0848f55ad8f3.png)

MSAA 并不会真的提高分辨率，只是通过细分一个像素为“多个像素”，方便去近似计算三角形在该像素的占比

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733422584087-4792985d-6bf0-4f4c-ad16-3a0106c9dceb.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733422606838-6d898ff0-d575-45f8-afdf-7d4ccaab2fbf.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733422618124-ace24fd1-9d74-4cc0-8ad2-73ff065471a1.png)

不同占比下，得到的像素值是不同的

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733422661911-9ce2e029-a2c3-485a-b841-928971dabf49.png)

通过 MSAA 无法提高实际的像素占比，但通过占比求平均像素值的方式，在一定程度上反走样了！

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733422725540-5a66997a-c005-4390-a69a-40ea4f4a951b.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733423623644-8e2ce7b1-cc0b-4a8b-8337-496108ea7f3f.png)

拉伸图片，超出原有的分辨率后，图片会变模糊，而解决这一问题的方式就叫超分辨率。

深度学习对此就比较擅长。

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733423850748-985775ba-0dc5-4dc9-a129-44b388007766.png)

拉伸一个图片，当他超出原有分辨率后，图片变模糊的原因：

当拉伸图片时，会通过不同的算法去填充新扩展的像素，而传统方法中，以最近邻插值来举例为什么会模糊。

以下是最近邻插值过程中原始图像和放大后的图像的值，逐步展示变化：

### 1. 原始图像（5x5 像素）

每个值表示一个像素的强度或颜色：

```plain
1  1  1  1  1
1  1  1  1  1
1  1  2  2  2
2  2  2  2  2
2  2  2  2  2
```

### 2. 放大后的图像（10x10 像素，最近邻插值，2倍放大）

每个原始像素变成4个相同的像素（2x2 的区域）：

```plain
1  1  1  1  1  1  1  1  1  1
1  1  1  1  1  1  1  1  1  1
1  1  1  1  1  1  1  1  1  1
1  1  1  1  1  1  1  1  1  1
1  1  1  1  2  2  2  2  2  2
1  1  1  1  2  2  2  2  2  2
2  2  2  2  2  2  2  2  2  2
2  2  2  2  2  2  2  2  2  2
2  2  2  2  2  2  2  2  2  2
2  2  2  2  2  2  2  2  2  2
```

### 变化分析

- **每个原始像素扩展**：

- 比如，原始图像中 `(1,1)` 的像素值为 `1`，在放大后变成一个 `2x2` 的区域：

```plain
1  1
1  1
```

- 类似地，原始像素值 `2` 被扩展为一个 `2x2` 的区域。

- **视觉效果**：

- 放大后的图像呈现“块状感”（每个像素被复制，没有过渡）。

- 边界（如 `1` 和 `2` 交界处）显得生硬，缺乏平滑过渡。

这就是最近邻插值方法简单拉伸像素的过程和效果。
