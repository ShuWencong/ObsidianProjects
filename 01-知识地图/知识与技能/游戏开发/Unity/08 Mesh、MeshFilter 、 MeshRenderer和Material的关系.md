---
title: "Mesh、MeshFilter 、 MeshRenderer和Material的关系"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/gpg0schumdqw7sp2"
slug: "gpg0schumdqw7sp2"
doc_id: "198511938"
updated: "2024-12-13T07:42:58.000Z"
tags:
  - yuque
---

# Mesh、MeshFilter 、 MeshRenderer和Material的关系

在 Unity 中，`Mesh`、`MeshFilter`、`MeshRenderer` 和 `Material` 是 3D 对象渲染的核心组件，它们各自承担不同的职责，但相互配合实现最终的视觉效果。以下是它们之间的关系和作用：

### 1. Mesh（网格）

- **定义：**

- `Mesh` 是 3D 模型的几何数据，包含顶点、边、面等信息。

- 它定义了一个物体的形状和结构，比如一个立方体、球体或自定义模型。

- **主要组成：**

- **顶点（Vertices）：** 决定网格的形状。

- **三角形（Triangles）：** 决定顶点之间如何连接，形成面。

- **法线（Normals）：** 决定光照方向。

- **UV 坐标：** 决定贴图如何映射到网格上。

- **作用：** 描述物体的几何形状。

### 2. MeshFilter（网格过滤器）

- **定义：**

- `MeshFilter` 是 Unity 的一个组件，用于将 `Mesh` 分配到一个对象上。

- 它是网格数据和游戏对象之间的桥梁。

- **作用：**

- `MeshFilter` 挂载在一个 GameObject 上，用于指定该对象使用哪个 `Mesh` 数据。

- **关键点：**

- 没有 `MeshFilter` 的 GameObject 无法显示自定义网格（对于 3D 物体）。

- 常见用法是将 `MeshFilter.sharedMesh` 设置为一个具体的 `Mesh`。

### 3. MeshRenderer（网格渲染器）

- **定义：**

- `MeshRenderer` 是 Unity 的另一个组件，用于渲染通过 `MeshFilter` 指定的网格。

- 它负责将网格显示在屏幕上，并应用材质、纹理等外观效果。

- **作用：**

- 决定网格在场景中的显示方式（如颜色、纹理、透明度等）。

- 它可以管理灯光、阴影和渲染设置。

- **关键点：**

- 没有 `MeshRenderer`，即使有 `MeshFilter` 和 `Mesh`，物体也不会渲染到屏幕上。

- `MeshRenderer` 通常和 `MeshFilter` 一起使用。

### 4. Material（材质）

- **定义：**

- `Material` 定义了物体表面的外观属性，包括颜色、纹理、光照、透明度等。

- 它使用一个或多个 **Shader** 来描述如何渲染表面。

- **作用：**

- 决定了物体的视觉效果。

- 材质中可以附加纹理贴图（Texture），比如砖墙、木纹。

- **关键点：**

- `MeshRenderer` 需要至少一个 `Material`，否则网格会以默认灰色显示。

- 一个网格可以使用多个材质（通过子网格实现）。

### 它们之间的关系

以下是它们之间的逻辑关系：

- `Mesh`**（形状）：** 定义了物体的几何数据。

- `MeshFilter`**（桥梁）：** 绑定 `Mesh` 到 GameObject。

- `MeshRenderer`**（显示）：** 将绑定的 `Mesh` 渲染到屏幕上。

- `Material`**（外观）：** 决定网格的表面视觉效果（颜色、纹理等）。

#### 关系示意：

```plain
Mesh (定义几何形状)
   ↓
MeshFilter (将几何绑定到对象)
   ↓
MeshRenderer (负责渲染)
   ↓
Material (控制外观效果，如颜色、纹理、光照)
```

### 场景中的示例

假设你在场景中创建了一个立方体：

- Unity 为立方体自动生成了一个 `Mesh`，包含立方体的顶点、面和 UV 数据。

- `MeshFilter` 组件将这个立方体网格（`Mesh`）附加到 GameObject 上。

- `MeshRenderer` 组件负责将立方体渲染到屏幕上。

- `Material` 定义立方体的颜色、光照效果或纹理，例如砖块纹理。

### 代码设置示例

以下是如何通过代码实现上述流程的示例：

```csharp
void Start() {
    // 创建 GameObject
    GameObject cube = new GameObject("CustomCube");

    // 添加 MeshFilter 组件
    MeshFilter meshFilter = cube.AddComponent();
    meshFilter.mesh = CreateCustomMesh(); // 使用自定义网格

    // 添加 MeshRenderer 组件
    MeshRenderer meshRenderer = cube.AddComponent();

    //不用将MeshFilter赋值给MeshRenderer，因为Unity已经自动关联好了

    // 创建并分配 Material
    Material material = new Material(Shader.Find("Standard"));
    material.color = Color.red;
    meshRenderer.material = material; // 设置材质
}

Mesh CreateCustomMesh() {
    // 创建一个简单的立方体网格
    Mesh mesh = new Mesh();
    mesh.vertices = new Vector3[] {
        new Vector3(-0.5f, -0.5f, 0.5f),
        new Vector3(0.5f, -0.5f, 0.5f),
        // 添加更多顶点...
    };
    mesh.triangles = new int[] {
        0, 1, 2, // 添加三角形
        // 添加更多三角形...
    };
    mesh.RecalculateNormals();
    return mesh;
}
```

### 总结

- `Mesh`：定义形状。

- `MeshFilter`：桥梁，绑定 `Mesh`。

- `MeshRenderer`：渲染，显示网格。

- `Material`：控制外观。

四者相互配合，共同实现 Unity 中 3D 对象的渲染。
