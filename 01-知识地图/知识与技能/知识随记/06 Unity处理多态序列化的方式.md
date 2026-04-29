---
title: "Unity处理多态序列化的方式"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/vosp7qy7u1uqtcf3"
slug: "vosp7qy7u1uqtcf3"
doc_id: "207204397"
updated: "2025-02-23T10:05:02.000Z"
tags:
  - yuque
---

# Unity处理多态序列化的方式

在 Unity 中解决多态序列化问题（如 `List` 包含不同子类对象），需根据引擎版本和需求选择以下方案：

### 一、内置方案

#### 1. [SerializeReference] 属性（Unity 2019.3+）

- **适用场景**：直接支持接口、抽象类或父类引用子类对象的序列化。

- **实现方式**：

```csharp
[SerializeReference]
public List entities = new List();
```

- **特性**：

- 序列化时保留实际子类类型信息。

- 在 Inspector 中显示多态对象的具体类型，支持动态替换子类。

- **限制**：不支持静态字段、非 `UnityEngine.Object` 类型的多态引用。

#### 2. ISerializationCallbackReceiver 接口

- **适用场景**：需手动控制序列化逻辑（如字典、多态集合）。

- **实现步骤**：

```csharp
public class PolymorphicList : MonoBehaviour, ISerializationCallbackReceiver {
    [SerializeField] private List _serializedData;
    private List _entities = new List();

    public void OnBeforeSerialize() {
        _serializedData = _entities.Select(e => Protobuf.Serialize(e)).ToList();
    }

    public void OnAfterDeserialize() {
        _entities = _serializedData.Select(b => Protobuf.Deserialize(b)).ToList();
    }
}
```

- 在类中实现 `OnBeforeSerialize` 和 `OnAfterDeserialize` 方法。

- 将多态数据转换为 Unity 可序列化的中间格式（如二进制或 JSON）。

- **优势**：兼容旧版本 Unity，支持复杂数据转换。

- **缺点**：需手动维护序列化逻辑，增加代码复杂度。

### 二、第三方工具方案

#### 3. Odin Inspector 插件

- **功能**：

- 直接序列化多态类型（包括接口、泛型集合）。

- 提供可视化编辑器支持，自动识别子类类型。

- **实现示例**：

```csharp
[ShowInInspector, SerializeField]
private List _humanList; // 直接支持接口类型序列化
```

- **优势**：简化开发流程，支持循环引用和复杂数据结构。

#### 4. JSON/二进制序列化库

- **推荐库**：Newtonsoft.Json、Protobuf-Net。

- **步骤**：

```csharp
[SerializeField] private string _jsonData;
private List _entities;

void Save() {
    _jsonData = JsonConvert.SerializeObject(_entities, new JsonSerializerSettings { TypeNameHandling = TypeNameHandling.Auto });
}

void Load() {
    _entities = JsonConvert.DeserializeObject>(_jsonData, new JsonSerializerSettings { TypeNameHandling = TypeNameHandling.Auto });
}
```

- 将多态数据序列化为 JSON 或二进制格式。

- 存储为字符串或字节数组字段供 Unity 序列化。

- **优势**：跨平台兼容性强，适合网络传输或存档。

### 三、兼容性与性能优化

- **版本迁移兼容性**

- 使用 `[FormerlySerializedAs]` 处理字段重命名，避免旧数据丢失。

- **性能权衡**

- **二进制序列化**（如 Protobuf）效率高，但需预定义类型。

- **JSON 序列化**可读性好，但数据体积较大。

- **ScriptableObject 扩展**

- 将多态数据封装为 ScriptableObject 资产，利用 Unity 内置资源管理系统。

### 总结：方案选择指南

**需求场景**

**推荐方案**

**引用依据**

新版 Unity（2019.3+）

`[SerializeReference]`

旧版 Unity 或自定义逻辑

`ISerializationCallbackReceiver`

复杂数据可视化编辑

Odin Inspector

跨平台或网络传输

Newtonsoft.Json/Protobuf

具体实现时需结合项目版本、性能要求及团队技术栈综合决策。
