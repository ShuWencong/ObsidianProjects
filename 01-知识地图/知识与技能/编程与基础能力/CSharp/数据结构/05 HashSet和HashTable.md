---
title: "HashSet和HashTable"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/hoob3cqfeuqns9uf"
slug: "hoob3cqfeuqns9uf"
doc_id: "185184475"
updated: "2024-09-14T04:54:59.000Z"
tags:
  - yuque
---

# HashSet和HashTable

# 一.  HashSet和HashTable在使用上的区别

`HashSet` 和 `Hashtable` 是 C# 中两个不同的集合类型，它们在使用上有明显的区别。下面是它们的主要区别：

### 1. 用途和数据结构

- **HashSet**:

- `HashSet` 是一个泛型集合，用于存储唯一的元素。它不允许重复的元素存在，且元素没有特定的顺序。

- 它适用于需要存储一组不重复的元素并快速查找的情况。

- **Hashtable**:

- `Hashtable` 是一个非泛型的键值对集合，它允许使用键来快速查找对应的值。

- 每个键必须是唯一的，值可以是任意类型。键和值都是对象类型（`object`），这意味着需要进行类型转换。

- `Hashtable` 适用于需要通过键快速访问值的情况。

### 2. 类型安全

- **HashSet**:

- 是类型安全的，因为它是一个泛型集合，存储的元素类型在声明时已经确定。比如，`HashSet` 只能存储 `int` 类型的元素。

- **Hashtable**:

- 不是类型安全的，因为它存储的是键值对的 `object`，你可以将任何类型的对象作为键和值。这可能会导致运行时的类型转换异常。

### 3. 泛型支持

- **HashSet**:

- `HashSet` 是泛型的，支持任何类型的元素，并提供类型检查和编译时的安全性。

- **Hashtable**:

- `Hashtable` 是非泛型的集合类型，因此不提供编译时的类型安全性。

### 4. 线程安全性

- **HashSet**:

- 默认情况下，`HashSet` 不是线程安全的。如果需要在多线程环境中使用，需要手动实现同步机制。

- **Hashtable**:

- `Hashtable` 是线程安全的，它对大多数操作进行了同步处理。因此，在多线程环境下，`Hashtable` 可以直接使用而不需要额外的同步机制。然而，使用 `Hashtable` 的线程安全性可能会带来性能开销。

### 5. 替代选择

- **HashSet**:

- 通常没有直接的替代选择，因为 `HashSet` 专注于存储唯一元素。如果你需要键值对的存储结构，应该考虑 `Dictionary`。

- **Hashtable**:

- 自 .NET 2.0 引入泛型以来，`Dictionary` 通常被认为是 `Hashtable` 的泛型替代品，提供更好的性能和类型安全性。

### 6. 使用示例

   **HashSet:**

```csharp
HashSet numbers = new HashSet();
numbers.Add(1);
numbers.Add(2);
numbers.Add(2);  // 不会添加，因为2已经存在于集合中
```

   **Hashtable:**

```csharp
Hashtable hashtable = new Hashtable();
hashtable.Add("key1", "value1");
hashtable.Add("key2", 42);
string value1 = (string)hashtable["key1"];
int value2 = (int)hashtable["key2"];
```

### 总结

- `HashSet` 是一种泛型集合，适用于存储唯一且类型安全的元素。

- `Hashtable` 是一种非泛型的键值对集合，适用于需要通过键快速访问值的情况，但它不是类型安全的，通常建议使用 `Dictionary` 作为它的替代品。
