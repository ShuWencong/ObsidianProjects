---
title: "DFS和BFS"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/slr24pccygait3wx"
slug: "slr24pccygait3wx"
doc_id: "185990276"
updated: "2024-09-10T08:26:59.000Z"
tags:
  - yuque
---

# DFS和BFS

在树的遍历中，迭代法通常使用**栈**或**队列**，但具体使用哪种取决于所采用的遍历方式：

### 1. 栈（Stack）：

- **适用于深度优先遍历（DFS，Depth-First Search）**。

- 栈是一种“后进先出”（LIFO, Last In First Out）结构，非常适合模拟递归调用栈的行为。因此，当你用迭代法进行深度优先遍历时，通常使用栈来存储节点。

#### 常见的深度优先遍历方式：

- **前序遍历（Preorder Traversal）**：先访问根节点，再访问左子树，最后访问右子树。

- **中序遍历（Inorder Traversal）**：先访问左子树，再访问根节点，最后访问右子树。

- **后序遍历（Postorder Traversal）**：先访问左子树，再访问右子树，最后访问根节点。

在这些遍历方法中，栈用来追踪当前节点以及返回父节点的路径。

#### 示例：前序遍历的迭代实现

```csharp
public IList PreorderTraversal(TreeNode root) {
    IList result = new List();
    if (root == null) return result;

    Stack stack = new Stack();
    stack.Push(root);

    while (stack.Count > 0) {
        TreeNode node = stack.Pop();
        result.Add(node.val);

        // 注意这里先压入右子树，再压入左子树，确保左子树先处理
        if (node.right != null) stack.Push(node.right);
        if (node.left != null) stack.Push(node.left);
    }

    return result;
}
```

### 2. 队列（Queue）：

- **适用于广度优先遍历（BFS，Breadth-First Search）**，通常也叫做**层序遍历**。

- 队列是一种“先进先出”（FIFO, First In First Out）结构，适合按层次逐层处理节点。

- 在广度优先遍历中，每次遍历一个节点时，将其子节点依次加入队列，先访问父节点，再访问它的所有子节点，因此广度优先遍历通常使用队列。

#### 广度优先遍历（层序遍历）的迭代实现

```csharp
public IList> LevelOrder(TreeNode root) {
    IList> result = new List>();
    if (root == null) return result;

    Queue queue = new Queue();
    queue.Enqueue(root);

    while (queue.Count > 0) {
        int levelSize = queue.Count;
        IList currentLevel = new List();

        for (int i = 0; i ：

- 适用于深度优先搜索（DFS），如前序遍历、中序遍历、后序遍历。

- 模拟递归调用栈，逐步深入到树的叶子节点。

- **队列**：

- 适用于广度优先搜索（BFS），即层序遍历。

- 逐层遍历树中的节点，确保按层顺序处理每个节点。
