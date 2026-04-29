---
title: "XLua"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/rzhtk3nyq51isk3n"
slug: "rzhtk3nyq51isk3n"
doc_id: "188038195"
updated: "2024-12-22T16:24:07.000Z"
tags:
  - yuque
---

# XLua

- AB 打包

我们点击打包时，会把 BuildeRes 文件夹下的所有文件打包，每个文件一个 ab 包（打包粒度太小），对应一个 AssetBundleBuild，存入 AssetBundles （Asset 下的相对路径）和 BundleName（BuildRes 下的相对路径加.ab），并且遍历所有依赖（不包含自身和.meta 还有.cs），同时将每个 assetBundle|bundleName.ab 存入 List<string>中。打包是使用BuildPipeline.BuildAssetBundles 方法实现打包，打包完成后，再将这个List<string>存入版本文件中。
