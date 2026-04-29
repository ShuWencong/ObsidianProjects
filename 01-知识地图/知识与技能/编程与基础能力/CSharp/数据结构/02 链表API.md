---
title: "链表API"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/rilrt8m0u8w0fwgk"
slug: "rilrt8m0u8w0fwgk"
doc_id: "186561620"
updated: "2024-09-14T04:50:21.000Z"
tags:
  - yuque
---

# 链表API

在 C# 中，链表的操作主要通过 `LinkedList` 类来实现，它提供了一系列的方法和属性来方便地操作链表。下面是一些常用的 `LinkedList` 相关的 API 操作示例：

### 创建链表和基本操作

#### 1. 创建链表和添加元素

```csharp
// 创建一个空的链表
LinkedList linkedList = new LinkedList();

// 向链表尾部添加元素
linkedList.AddLast(1);
linkedList.AddLast(2);
linkedList.AddLast(3);
```

#### 2. 遍历链表元素

```csharp
// 遍历链表元素
LinkedListNode currentNode = linkedList.First;
while (currentNode != null)
{
    Console.WriteLine(currentNode.Value);
    currentNode = currentNode.Next;
}
```

### 常用方法和属性

#### 1. 添加元素

- `AddFirst(T value)`: 在链表头部添加元素。

- `AddLast(T value)`: 在链表尾部添加元素。

```csharp
linkedList.AddFirst(0); // 在头部添加元素
linkedList.AddLast(4);  // 在尾部添加元素
```

#### 2. 删除元素

- `RemoveFirst()`: 移除链表的第一个元素。

- `RemoveLast()`: 移除链表的最后一个元素。

- `Remove(LinkedListNode node)`: 移除指定的节点。

```csharp
linkedList.RemoveFirst(); // 移除第一个元素
linkedList.RemoveLast();  // 移除最后一个元素

// 移除指定节点
LinkedListNode nodeToRemove = linkedList.First.Next;
linkedList.Remove(nodeToRemove);
```

#### 3. 访问元素和节点

- `First`: 获取链表的第一个节点。

- `Last`: 获取链表的最后一个节点。

- `Count`: 获取链表中元素的数量。

```csharp
LinkedListNode firstNode = linkedList.First;
LinkedListNode lastNode = linkedList.Last;
int count = linkedList.Count;
```

#### 4. 查找元素

- `Find(T value)`: 查找链表中第一个与指定值匹配的节点。

- `Contains(T value)`: 判断链表是否包含指定值。

```csharp
LinkedListNode foundNode = linkedList.Find(2); // 查找值为 2 的节点
bool containsValue = linkedList.Contains(3); // 判断是否包含值为 3 的节点
```

#### 5. 清空链表

- `Clear()`: 清空链表中的所有元素。

```csharp
linkedList.Clear(); // 清空链表
```

### 示例总结

```csharp
using System;

class Program
{
    static void Main()
    {
        // 创建一个整数类型的链表
        LinkedList linkedList = new LinkedList();

        // 添加元素
        linkedList.AddLast(1);
        linkedList.AddLast(2);
        linkedList.AddLast(3);

        // 遍历链表并输出元素
        LinkedListNode currentNode = linkedList.First;
        while (currentNode != null)
        {
            Console.WriteLine(currentNode.Value);
            currentNode = currentNode.Next;
        }

        // 其他操作...
    }
}
```

以上是一些常见的 `LinkedList` 类的使用方法和示例，可以根据具体需求和场景选择合适的操作来操作链表。
