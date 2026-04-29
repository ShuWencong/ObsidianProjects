---
title: "[AddComponentMenu(\"\")]"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/ahuy267dsopxwvax"
slug: "ahuy267dsopxwvax"
doc_id: "207200484"
updated: "2025-02-23T09:19:46.000Z"
tags:
  - yuque
---

# [AddComponentMenu("")]

[AddComponentMenu("")]

- [链接](about:blank)**隐藏组件菜单项**
当 `AddComponentMenu` 特性的路径参数设为空字符串时，该组件**不会出现在 Unity 编辑器的 Component 菜单中**，即从菜单中完全隐藏

- **典型场景**：

- 不希望用户通过编辑器手动添加该组件，例如抽象基类或仅供代码动态添加的工具类组件。

- 需要将组件作为其他功能的依赖项，但无需直接暴露给开发者。
