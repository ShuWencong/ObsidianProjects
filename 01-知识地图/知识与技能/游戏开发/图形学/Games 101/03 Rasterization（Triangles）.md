---
title: "Rasterization（Triangles）"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/mmrnzgo9smsgqppn"
slug: "mmrnzgo9smsgqppn"
doc_id: "197453776"
updated: "2024-12-05T16:42:51.000Z"
tags:
  - yuque
---

# Rasterization（Triangles）

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415150257-e50acd45-0682-48dd-98e9-ec642b89afde.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415385182-b54b0ae7-982b-4aca-8a13-8e479f82018e.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415432369-a4640df0-de87-40a9-a829-317b9d0c0d50.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415451986-1efbd517-9cf4-44ee-aaa8-2c0578f38e7e.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415646530-3cd39e8c-12c6-46e9-9c2a-12cbb2df45dd.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415682874-d27ce2bc-804e-4c12-a4b7-a248533c3cdf.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415707155-148c9d21-7bdc-4d4b-a9d0-e7b1df409530.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415725177-c29f8097-2c1d-4c39-8414-5f56218e32f6.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415747866-a282b9b0-0792-4de1-84ba-d728d34b355b.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415830587-7ab49892-002f-46cd-a618-aa35face50b3.png)

通过采样的方式来将顶点位置信息转化为屏幕像素信息

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415847943-cce59f8c-59e1-48a9-ada9-cc7ce5870d60.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733415879179-b5dc7615-54d4-4961-9e89-bda0badf170d.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416000329-2c56f41d-1165-47cc-b0a5-920d6ba46a40.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416015265-6f2aa6e4-e5b1-4db1-a78b-5c1c431dfa52.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416032630-8f6fd542-fc5f-4c66-82f7-7ec56dbd9e35.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416086871-c3a1d5de-d9f6-4308-8e4c-009f3033e765.png)

通过叉乘的方法计算

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416106599-87d85a5d-ac8e-4009-84cb-b992a4860dd4.png)

对于这种某个点在两个三角形内时，需要一个规定，来规范该点属于哪个三角形。

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416129735-a4f5718e-7fc6-4094-a887-438510a5f934.png)

通过使用 AABB 包围盒，可以减少计算范围，在包围盒外的像素值直接为 0

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416239346-45a34c87-6608-4e25-9460-8453f9dcac7a.png)

另外一种方式，每次都从最左边到最右边去遍历，那么边界就需要去计算，但可以省去不必要的检测。

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416324242-4f3a18de-cb88-4798-b949-459940ea2179.png)

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416426243-9bbccc09-1627-4695-a639-11b720d9d1ca.png)

可以发现如果直接使用计算出的结果是会发生走样的！那么就需要使用对应的反走样方式去弥补这一缺陷。

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416441449-b01df84e-54d3-425f-adbb-84c1647fea3a.png)

放大图片可以明显看到发生了走样（存在锯齿）

![](https://cdn.nlark.com/yuque/0/2024/png/46628487/1733416457881-60ab09fa-27a8-4ceb-b3f4-180aaa854b7a.png)
