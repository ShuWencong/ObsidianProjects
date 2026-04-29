---
title: "数组，栈和队列API"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/ygw7rsq8g0g4g14e"
slug: "ygw7rsq8g0g4g14e"
doc_id: "186561715"
updated: "2024-09-14T04:53:36.000Z"
tags:
  - yuque
---

# 数组，栈和队列API

在 C# 中，**栈** (`Stack`)、**队列** (`Queue`)、和**数组** (`Array`) 都有各自的 API 来进行操作。以下是这些数据结构的常用 API 及其使用示例，帮助你理解它们的用法。

## 1. 栈 (Stack)

栈是一种 **后进先出（LIFO）** 的数据结构。

### 常用 API：

- `Push(T item)`: 将元素压入栈顶。

- `Pop()`: 移除并返回栈顶元素。

- `Peek()`: 返回栈顶元素，但不移除它。

- `Count`: 获取栈中的元素数量。

- `Clear()`: 清空栈中的所有元素。

- `Contains(T item)`: 判断栈是否包含指定元素。

- `ToArray()`: 将栈转换为数组。

### 示例：

```csharp
Stack stack = new Stack();

// 压入元素
stack.Push(1);
stack.Push(2);
stack.Push(3);

// 查看栈顶元素（不移除）
int topElement = stack.Peek(); // 输出 3

// 移除并返回栈顶元素
int poppedElement = stack.Pop(); // 输出 3

// 获取栈中元素的数量
int count = stack.Count; // 输出 2

// 判断栈是否包含某个元素
bool containsTwo = stack.Contains(2); // 输出 true

// 清空栈
stack.Clear();
```

## 2. 队列 (Queue)

队列是一种 **先进先出（FIFO）** 的数据结构。

### 常用 API：

- `Enqueue(T item)`: 将元素添加到队列的末尾。

- `Dequeue()`: 移除并返回队列的头部元素。

- `Peek()`: 返回队列的头部元素，但不移除它。

- `Count`: 获取队列中的元素数量。

- `Clear()`: 清空队列中的所有元素。

- `Contains(T item)`: 判断队列是否包含指定元素。

- `ToArray()`: 将队列转换为数组。

### 示例：

```csharp
Queue queue = new Queue();

// 入队
queue.Enqueue(1);
queue.Enqueue(2);
queue.Enqueue(3);

// 查看队列头部元素（不移除）
int headElement = queue.Peek(); // 输出 1

// 移除并返回队列头部元素
int dequeuedElement = queue.Dequeue(); // 输出 1

// 获取队列中元素的数量
int count = queue.Count; // 输出 2

// 判断队列是否包含某个元素
bool containsTwo = queue.Contains(2); // 输出 true

// 清空队列
queue.Clear();
```

## 3. 数组 (Array)

数组是固定大小的线性数据结构，元素类型可以是任意类型。

### 常用 API：

- `Length`: 获取数组的长度（元素的个数）。

- `IndexOf(T[] array, T value)`: 查找元素在数组中的索引（需要引入 `System.Array`）。

- `Sort(T[] array)`: 对数组进行排序。

- `Reverse(T[] array)`: 将数组元素的顺序反转。

- `Copy(T[] sourceArray, T[] destinationArray, int length)`: 将一个数组的元素复制到另一个数组中。

- `Clear(T[] array, int index, int length)`: 将数组中的元素设置为默认值。

- `ToArray()`: 将列表等集合类型转换为数组。

### 示例：

```csharp
int[] array = { 1, 3, 5, 7, 9 };

// 获取数组长度
int length = array.Length; // 输出 5

// 查找数组中元素的索引
int index = Array.IndexOf(array, 5); // 输出 2

// 对数组进行排序
Array.Sort(array);

// 反转数组元素
Array.Reverse(array);

// 复制数组
int[] newArray = new int[5];
Array.Copy(array, newArray, 5);

// 清空数组的元素
Array.Clear(newArray, 0, newArray.Length); // 数组元素被设置为 0
```

### 总结：

#### 栈 (Stack) 的常用 API:

- `Push(T item)`: 压栈

- `Pop()`: 弹栈

- `Peek()`: 获取栈顶元素（不移除）

- `Count`: 获取元素数量

- `Clear()`: 清空栈

- `Contains(T item)`: 判断是否包含某元素

- `ToArray()`: 转换为数组

#### 队列 (Queue) 的常用 API:

- `Enqueue(T item)`: 入队

- `Dequeue()`: 出队

- `Peek()`: 获取队列头部元素（不移除）

- `Count`: 获取元素数量

- `Clear()`: 清空队列

- `Contains(T item)`: 判断是否包含某元素

- `ToArray()`: 转换为数组

#### 数组 (Array) 的常用 API:

- `Length`: 获取数组长度

- `IndexOf(T[] array, T value)`: 查找元素索引

- `Sort(T[] array)`: 排序

- `Reverse(T[] array)`: 反转

- `Copy(T[] sourceArray, T[] destinationArray, int length)`: 复制数组

- `Clear(T[] array, int index, int length)`: 清空数组内容

通过这些常见 API，你可以很方便地操作栈、队列和数组。希望这些内容能够帮助你掌握相关知识！
