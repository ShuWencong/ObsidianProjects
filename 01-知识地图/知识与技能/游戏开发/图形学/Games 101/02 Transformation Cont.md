---
title: "Transformation Cont"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/uncpfvele91m7ycl"
slug: "uncpfvele91m7ycl"
doc_id: "197122401"
updated: "2024-12-03T18:56:42.000Z"
tags:
  - yuque
---

# Transformation Cont

1.R 的 逆等于 R 的转置，这个也叫做正交矩阵

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733236250971-790b761a-7a16-4900-be04-c3941e48fe51.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733236395721-259939a8-e764-4e41-9ffa-870fca87a666.png)

2.三维空间中的缩放和平移

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733236513553-5ce5c0d7-3659-4f10-96ca-a4c5c5ceddd9.png)

3.三维空间下的旋转

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733236885107-f90f66c6-f7f0-4a4f-942d-5afd59f3d136.png)

MVP 变换（模型，视图，投影变化）

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733240911786-a6b5e369-3ea8-4746-b5e4-b6bb6b03747c.png)

视图变换

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733242468130-dfeb6e40-d224-4715-8061-41aff12d6008.png)

固定相机位置，相机朝向，相机向上方向

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733241046449-e5ea18bd-467e-4de1-a2c0-dff5cc70932e.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733241219760-4b46345d-ca41-44ab-b10f-538c42bde595.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733241387660-18855e90-e57f-4842-b9a3-3f167ce6a231.png)

先平移，然后旋转，但直接改变轴的旋转有点复杂，因此，反过来写，由标准轴转化为相机的朝向，然后因为旋转的矩阵是正交矩阵，所以，可以直接转置，转置就会等于该旋转的逆。

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733242130973-d3ebb254-c125-4f21-97ea-064e2d580339.png)

正交投影和透视投影

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733248284309-80e98a01-1ac8-4ac1-b084-a0445d07dd99.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733248448572-dc6ccf9b-3dcc-4257-b054-e21b4aac6511.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733248467040-e71f6444-389a-42d3-96f1-374c3a097a35.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733248711179-ff2e8962-0a32-4d57-b324-238212005f46.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733249183769-352c02b1-684b-471f-805a-d7ffb6d4d623.png)

先挤压所有的点到正交位置，在做一次正交投影

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733249248749-23d82b54-d2ed-4664-a530-58d4e456381f.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733249869783-6d12dce0-ea32-4903-9e9b-3fb3150faf39.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733249952668-856f3904-1df4-40cc-b9b4-139d8352aa69.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733250022889-30ff88ed-7c6f-4b9b-b609-996becb54557.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733250299699-7e4bed9b-f3a2-4df9-9025-7619bbc8d69f.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733251258952-0e35fabf-f490-46a1-9581-929af9c802e6.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733251788645-e2ccaedc-bfbc-4061-8a8d-c15642446f07.png)

解出了透视投影的变换矩阵值之后，再左乘一下正交投影变化的矩阵值即可

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733251958606-abce231f-6f89-44f8-a5b5-1f8bb247324a.png)
