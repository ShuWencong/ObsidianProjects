---
title: "ReadOnly和Const"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/vh4opompgpyh3dma"
slug: "vh4opompgpyh3dma"
doc_id: "207214241"
updated: "2025-02-23T12:22:05.000Z"
tags:
  - yuque
---

# ReadOnly和Const

在 C# 中，`readonly` 和 `const` 都用于定义常量，但它们在实现机制、使用场景和限制条件上有显著差异。以下是两者的核心区别及适用场景总结：

### 1. 初始化时机与赋值限制

**特性**

`const`

`readonly`

**引用依据**

**初始化时机**

必须在声明时直接初始化。

可在声明时或构造函数中初始化。

**赋值限制**

值一旦设定不可更改。

只能在声明或构造函数中赋值一次。

**示例**

`const int MaxValue = 100;`

`readonly int _value = 200;`

### 2. 类型限制与作用域

**特性**

`const`

`readonly`

**引用依据**

**支持类型**

仅限基元类型（如 `int`、`string`）、枚举或 `null`。

支持所有类型（包括引用类型和复杂对象）。

**作用域**

隐式静态（`static`），只能在类级别声明。

可以是实例字段或显式静态字段。

**示例**

`public const string Name = "C#";`

`public readonly List Numbers = new();`

### 3. 存储方式与运行时行为

**特性**

`const`

`readonly`

**引用依据**

**存储方式**

编译时直接替换为字面值（无内存分配）。

运行时分配内存存储实际值。

**多程序集影响**

修改 `const` 需重新编译所有依赖程序集。

修改 `readonly` 仅需重新编译当前程序集。

**示例**

若 `const` 值改变，依赖代码需重新编译。

`readonly` 值在运行时动态解析。

### 4. 性能与灵活性

**特性**

`const`

`readonly`

**引用依据**

**性能**

更高（编译时优化，无运行时开销）。

稍低（需运行时解析和内存分配）。

**灵活性**

不灵活（硬编码值，无法动态计算）。

灵活（允许运行时计算和对象初始化）。

**示例**

`const int Result = 10 * 20;`

`readonly int Result = CalculateValue();`

### 5. 引用类型的行为差异

**特性**

`const`

`readonly`

**引用依据**

**引用类型**

仅支持 `string` 和 `null`。

支持任何引用类型（如类实例）。

**可变性**

不可变（值或引用均不可修改）。

引用不可变，但对象内部状态可修改。

**示例**

`const string Path = "/data";`

`readonly List _list = new();`（可添加元素）

### 总结：如何选择？

- **优先 **`const`：

- 适用于简单、确定不变的值（如数学常数、配置标志）。

- 需跨程序集共享且不频繁修改的场景。

- **示例**：`public const float Pi = 3.14159f;` 。

- **优先 **`readonly`：

- 需运行时计算或依赖构造函数初始化的场景。

- 引用类型常量或需要对象内部状态可变的情况。

- **示例**：`public readonly DateTime CreatedAt = DateTime.Now;` 。

- **混合使用 **`static readonly`：

- 替代 `const` 以提升灵活性，同时保持类级别的静态性。

- **示例**：`public static readonly int MaxRetries = 3;` 。

### 附：关键区别速查表

**维度**

`const`

`readonly`

**初始化时机**

声明时

声明时或构造函数中

**类型支持**

基元类型、枚举、字符串

所有类型

**内存分配**

无（编译时替换）

有（运行时分配）

**多态支持**

否

是（允许不同实例不同值）

**跨程序集影响**

需重新编译依赖项

无需重新编译依赖项

通过合理选择 `const` 和 `readonly`，可以在代码性能与灵活性之间取得平衡。
