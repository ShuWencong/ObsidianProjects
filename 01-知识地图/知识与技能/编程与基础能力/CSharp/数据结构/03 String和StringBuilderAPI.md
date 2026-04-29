---
title: "String和StringBuilderAPI"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/luwoy82zgkcvznzb"
slug: "luwoy82zgkcvznzb"
doc_id: "186560761"
updated: "2024-09-14T07:26:42.000Z"
tags:
  - yuque
---

# String和StringBuilderAPI

# 一、 String 的 API

在 C# 中，`string` 是一个非常常用的类，提供了许多有用的方法和属性。以下是一些常见且实用的 `string` 相关 API，按照不同功能分类介绍，便于记忆和理解。

### 1. 创建和操作字符串

- `string.Concat()`: 将多个字符串或字符连接在一起。

```csharp
string result = string.Concat("Hello", " ", "World"); // 输出: "Hello World"
```

- `string.Join()`: 使用指定的分隔符连接数组或集合中的元素。

```csharp
string[] words = { "Hello", "World" };
string result = string.Join(", ", words); // 输出: "Hello, World"
```

- `string.Format()`: 将字符串格式化，插入动态内容。

```csharp
string result = string.Format("My name is {0} and I am {1} years old", "John", 30);
// 输出: "My name is John and I am 30 years old"
```

- `$"interpolated string"`: 字符串插值的简写方式，允许在字符串中插入变量。

```csharp
string name = "John";
int age = 30;
string result = $"My name is {name} and I am {age} years old";
// 输出: "My name is John and I am 30 years old"
```

### 2. 字符串检查

- `string.IsNullOrEmpty()`: 检查字符串是否为 `null` 或空。

```csharp
string str = "";
bool isNullOrEmpty = string.IsNullOrEmpty(str); // 输出: true
```

- `string.IsNullOrWhiteSpace()`: 检查字符串是否为 `null`、空或仅包含空白字符。

```csharp
string str = "   ";
bool isNullOrWhiteSpace = string.IsNullOrWhiteSpace(str); // 输出: true
```

### 3. 字符串搜索

- `string.Contains()`: 检查字符串是否包含指定的子字符串。

```csharp
string str = "Hello World";
bool contains = str.Contains("World"); // 输出: true
```

- `string.IndexOf()`: 查找子字符串在字符串中的第一个出现位置，返回索引值，找不到返回 `-1`。

```csharp
string str = "Hello World";
int index = str.IndexOf("World"); // 输出: 6
```

- `string.LastIndexOf()`: 查找子字符串最后一次出现的位置。

```csharp
string str = "Hello World World";
int index = str.LastIndexOf("World"); // 输出: 12
```

- `string.StartsWith()`** 和 **`string.EndsWith()`: 检查字符串是否以特定的子字符串开头或结尾。

```csharp
string str = "Hello World";
bool startsWith = str.StartsWith("Hello"); // 输出: true
bool endsWith = str.EndsWith("World");     // 输出: true
```

### 4. 字符串修改

- `string.Replace()`: 替换字符串中的子字符串。

```csharp
string str = "Hello World";
string result = str.Replace("World", "C#"); // 输出: "Hello C#"
```

- `string.Trim()`: 移除字符串两端的空白字符（可使用 `TrimStart()` 或 `TrimEnd()` 只去除一端的空白）。

```csharp
string str = "  Hello World  ";
string result = str.Trim(); // 输出: "Hello World"
```

- `string.ToLower()`** 和 **`string.ToUpper()`: 转换字符串为小写或大写字母。

```csharp
string str = "Hello World";
string lower = str.ToLower(); // 输出: "hello world"
string upper = str.ToUpper(); // 输出: "HELLO WORLD"
```

- `string.Insert()`: 在指定索引位置插入字符串。

```csharp
string str = "Hello World";
string result = str.Insert(5, ", Beautiful"); // 输出: "Hello, Beautiful World"
```

- `string.Remove()`: 从指定位置开始删除指定数量的字符。

```csharp
string str = "Hello World";
string result = str.Remove(5, 6); // 输出: "Hello"
```

- `string.Substring()`: 提取子字符串，从指定的索引位置开始。

```csharp
string str = "Hello World";
string result = str.Substring(6);  // 输出: "World"
string part = str.Substring(0, 5); // 输出: "Hello"
```

### 5. 字符串分割

- `string.Split()`: 将字符串按照分隔符拆分成数组。

```csharp
string str = "Hello,World,C#";
string[] parts = str.Split(','); // 输出: ["Hello", "World", "C#"]
```

### 6. 字符串长度

- `string.Length`: 获取字符串的长度。

```csharp
string str = "Hello World";
int length = str.Length; // 输出: 11
```

### 7. 字符串比较

- `string.Compare()`: 比较两个字符串，返回一个整数，指示第一个字符串是否小于、等于或大于第二个字符串。

```csharp
string str1 = "apple";
string str2 = "banana";
int comparison = string.Compare(str1, str2); // 输出: -1 （apple 小于 banana）
```

- `string.Equals()`: 比较两个字符串是否相等，支持忽略大小写的比较。

```csharp
string str1 = "Hello";
string str2 = "hello";
bool areEqual = str1.Equals(str2, StringComparison.OrdinalIgnoreCase); // 输出: true
```

### 8. 字符串转义和操作

- `string.Escape()`: 添加字符串转义符，如 `\n` 换行符。

```csharp
string str = "Hello\nWorld"; // 输出: Hello (换行) World
```

- `@`** 符号（逐字字符串）**: 创建包含特殊字符的字符串，忽略转义符。

```csharp
string path = @"C:\Program Files\MyApp"; // 输出: C:\Program Files\MyApp
```

### 总结：

- **创建/拼接**: `Concat()`, `Join()`, `$"interpolated"`, `Format()`

- **检查/搜索**: `IsNullOrEmpty()`, `Contains()`, `IndexOf()`, `StartsWith()`, `EndsWith()`

- **修改/操作**: `Replace()`, `Trim()`, `ToLower()`, `ToUpper()`, `Insert()`, `Remove()`, `Substring()`

- **分割**: `Split()`

- **长度**: `Length`

- **比较**: `Compare()`, `Equals()`

这些常见的 `string` API 覆盖了大多数操作字符串的需求，记住这些会帮助你轻松处理各种字符串操作任务。

抱歉，之前我解释的是 Java 中的 `StringBuilder`。现在我来为你介绍 C# 中的 `StringBuilder`。

在 C# 中，`StringBuilder` 类位于 `System.Text` 命名空间中，主要用于处理需要频繁修改的字符串。这与 `String` 不同，后者是不可变的，任何修改都会创建一个新的字符串实例，而 `StringBuilder` 允许直接修改字符串，从而提升性能。

# 二、StringBuilder 的 API

### 常用的 StringBuilder API 列表

#### 1. 构造方法

- `StringBuilder()`
初始化一个空的 `StringBuilder` 实例，初始容量为 16。

- `StringBuilder(int capacity)`
初始化一个具有指定初始容量的 `StringBuilder` 实例。

- `StringBuilder(string value)`
使用指定的字符串初始化 `StringBuilder`。

- `StringBuilder(string value, int capacity)`
用指定的字符串初始化 `StringBuilder`，并设置容量。

#### 2. 基本属性

- `int Length`
获取或设置当前字符串的长度。

- `int Capacity`
获取或设置 `StringBuilder` 的容量，即它能够在不重新分配内存的情况下存储的字符数量。

- `int MaxCapacity`
获取 `StringBuilder` 可以存储的最大字符数量。

#### 3. 常用方法

##### 3.1 追加字符串

- `StringBuilder Append(string value)`
将指定的字符串追加到当前 `StringBuilder` 对象的末尾。常用的重载版本包括：

- `Append(char value)`

- `Append(int value)`

- `Append(bool value)`

- `Append(object value)` 等

- `StringBuilder AppendLine()`
在字符串末尾追加默认行结束符（即 `\n` 或 `\r\n`，取决于平台）。

- `StringBuilder AppendLine(string value)`
将指定的字符串追加到 `StringBuilder` 对象末尾，并随后追加行结束符。

##### 3.2 插入字符串

- `StringBuilder Insert(int index, string value)`
在指定位置插入字符串。常用的重载版本包括：

- `Insert(int index, char value)`

- `Insert(int index, int value)`

- `Insert(int index, bool value)` 等

##### 3.3 移除字符串

- `StringBuilder Remove(int startIndex, int length)`
删除从指定索引开始，长度为 `length` 的字符。

##### 3.4 替换字符串

- `StringBuilder Replace(string oldValue, string newValue)`
将 `StringBuilder` 中的所有 `oldValue` 子字符串替换为 `newValue`。常用的重载版本包括：

- `Replace(char oldChar, char newChar)`

- `Replace(string oldValue, string newValue, int startIndex, int count)`

##### 3.5 反转字符串

C# 的 `StringBuilder` 没有直接提供 `reverse()` 方法，如果你想反转，可以先将 `StringBuilder` 转换为 `string`，然后用字符数组手动反转，或者通过 `LINQ` 来实现。

##### 3.6 查询方法

- `char this[int index]`
获取或设置指定位置的字符。

#### 4. 转换方法

- `string ToString()`
将 `StringBuilder` 中的内容转换为 `string`。

#### 5. 清空内容

- `StringBuilder Clear()`
清除 `StringBuilder` 的内容，并将 `Length` 设置为 0。

### 示例代码

```csharp
using System;
using System.Text;

class Program
{
    static void Main()
    {
        // 创建StringBuilder对象
        StringBuilder sb = new StringBuilder("Hello");

        // Append方法
        sb.Append(" World");
        Console.WriteLine(sb); // 输出: Hello World

        // AppendLine方法
        sb.AppendLine("!");
        Console.WriteLine(sb); // 输出: Hello World!

        // Insert方法
        sb.Insert(6, "C# ");
        Console.WriteLine(sb); // 输出: Hello C# World!

        // Remove方法
        sb.Remove(5, 3); // 移除 " C#"
        Console.WriteLine(sb); // 输出: Hello World!

        // Replace方法
        sb.Replace("World", "StringBuilder");
        Console.WriteLine(sb); // 输出: Hello StringBuilder!

        // 获取字符串长度和容量
        Console.WriteLine($"Length: {sb.Length}, Capacity: {sb.Capacity}");

        // 转换为string
        string result = sb.ToString();
        Console.WriteLine(result); // 输出: Hello StringBuilder!

        // 清空StringBuilder
        sb.Clear();
        Console.WriteLine($"Cleared StringBuilder: '{sb}'");
    }
}
```

### 总结

- `StringBuilder` 是处理大量字符串修改时的首选，因为它可以避免创建大量临时的字符串对象。

- 常用方法包括：`Append()`、`Insert()`、`Remove()`、`Replace()` 和 `Clear()`。

- `StringBuilder` 提供了对容量的动态调整功能，可以手动控制容量以优化性能。

它通常用于高性能的字符串操作场景，比如字符串拼接、大量字符串更新等。
