---
title: "Nav问题"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/ycp330w76v7gr62z"
slug: "ycp330w76v7gr62z"
doc_id: "218915836"
updated: "2025-05-09T15:02:28.000Z"
tags:
  - yuque
---

# Nav问题

- Bake 出来的高度略高于实际地面，不过运行下来，看不太出来。

优化方案：1.调整体素大小，提高精度。2.勾选 BuildHeightMesh，保存高度信息。

- Bake 出来的地面不平整，有些平地还有三角面片凸起

优化方案：1.去除不必要的小物件影响到 Nav 的烘焙。   2. 也可以直接调整 IncludeLayer，主动勾选需要 Bake 的层。
