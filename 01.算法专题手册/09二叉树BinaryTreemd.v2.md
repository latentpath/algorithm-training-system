# 二叉树 Binary Tree

## 本章目标

训练树题第一反应：看到二叉树，先判断是“遍历、子树信息、路径、BST、LCA”中的哪一类。

## 秒判卡

| 看到什么 | 直接想到 |
|---|---|
| 层序 / 每层 | BFS 队列 |
| 深度 / 高度 | DFS 返回高度 |
| 子树是否平衡 / 直径 | 后序 DFS |
| 根到叶路径 | DFS 带路径或剩余值 |
| BST 第 k 小 | 中序遍历 |
| BST 合法性 | 上下界递归 |
| 最近公共祖先 | 左右子树找目标 |

## 高频模板 1：树 DFS 返回子树信息

### 秒判关键词

高度、节点数、最大深度、子树答案。

### 母题

LC104 Maximum Depth of Binary Tree

### 标准代码

```java
public int maxDepth(TreeNode root) {
    if (root == null) return 0;
    int left = maxDepth(root.left);
    int right = maxDepth(root.right);
    return Math.max(left, right) + 1;
}
```

### 一句话记忆

先要左右子树答案，再合成当前节点答案。

### 高频变体

| 题目 | 变化点 |
|---|---|
| Balanced Binary Tree | 后序返回高度，发现不平衡返回 -1 |
| Diameter of Binary Tree | 左高 + 右高更新答案 |
| Count Complete Tree Nodes | 普通 DFS 可做，完全树可优化 |

### 常见坑点

- 子树信息题通常是后序。
- 全局答案要在每个节点更新。

## 高频模板 2：树 BFS 层序

### 秒判关键词

每层、层序、最小深度、右视图。

### 母题

LC102 Binary Tree Level Order Traversal

### 标准代码

```java
public List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> ans = new ArrayList<>();
    if (root == null) return ans;

    Queue<TreeNode> queue = new ArrayDeque<>();
    queue.offer(root);
    while (!queue.isEmpty()) {
        int size = queue.size();
        List<Integer> level = new ArrayList<>();
        for (int i = 0; i < size; i++) {
            TreeNode node = queue.poll();
            level.add(node.val);
            if (node.left != null) queue.offer(node.left);
            if (node.right != null) queue.offer(node.right);
        }
        ans.add(level);
    }
    return ans;
}
```

### 一句话记忆

队列按层处理，`size` 固定当前层。

### 高频变体

- Right Side View：每层最后一个节点。
- Minimum Depth：第一次遇到叶子返回层数。
- Zigzag Level Order：奇偶层反向加入。

### 常见坑点

- 不保存 `size` 会把下一层混进当前层。
- 空树先返回空结果。

## 高频模板 3：路径 DFS

### 秒判关键词

根到叶、路径和、收集路径、从上往下。

### 母题

LC112 Path Sum

### 标准代码

```java
public boolean hasPathSum(TreeNode root, int targetSum) {
    if (root == null) return false;
    if (root.left == null && root.right == null) {
        return targetSum == root.val;
    }
    int next = targetSum - root.val;
    return hasPathSum(root.left, next) || hasPathSum(root.right, next);
}
```

### 一句话记忆

一路往下减，到叶子时检查是否刚好用完。

### 高频变体

| 题目 | 变化点 |
|---|---|
| Path Sum II | 用 `path` 收集，返回前撤销 |
| Binary Tree Paths | 收集字符串路径 |
| Path Sum III | 前缀和 + HashMap |

### 常见坑点

- Path Sum I 必须到叶子才判断。
- 收集所有路径时要回溯撤销。
- Path Sum III 不是简单根到叶。

## 高频模板 4：BST 中序 / 上下界

### 秒判关键词

二叉搜索树、第 k 小、是否合法、范围。

### 母题

LC98 Validate Binary Search Tree

### 标准代码

```java
public boolean isValidBST(TreeNode root) {
    return valid(root, null, null);
}

private boolean valid(TreeNode node, Long low, Long high) {
    if (node == null) return true;
    long val = node.val;
    if (low != null && val <= low) return false;
    if (high != null && val >= high) return false;
    return valid(node.left, low, val) && valid(node.right, val, high);
}
```

### 一句话记忆

BST 不是只看左右孩子，要看整棵子树的上下界。

### 高频变体

- Kth Smallest：中序第 k 个。
- Search in BST：按大小走左或右。
- Lowest Common Ancestor of BST：利用大小关系分叉。

### 常见坑点

- 不要只判断 `left.val < root.val < right.val`。
- 用 `long` 或对象边界，避免极值溢出。

## 高频模板 5：最近公共祖先

### 秒判关键词

两个节点、最近公共祖先、左右子树找目标。

### 母题

LC236 Lowest Common Ancestor of a Binary Tree

### 标准代码

```java
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root == null || root == p || root == q) return root;

    TreeNode left = lowestCommonAncestor(root.left, p, q);
    TreeNode right = lowestCommonAncestor(root.right, p, q);

    if (left != null && right != null) return root;
    return left != null ? left : right;
}
```

### 一句话记忆

左右各找到一个，当前节点就是最近公共祖先。

### 高频变体

- BST LCA：用值大小直接走。
- 多节点 LCA：把目标放 Set。

### 常见坑点

- 普通二叉树不能用 BST 大小关系。
- 如果题目不保证节点存在，需要额外判断存在性。

## 高频坑点

| 坑点 | 正确反应 |
|---|---|
| 树题没处理 `root == null` | 先写 base case |
| 子树信息用前序硬算 | 改后序返回 |
| BST 只看孩子 | 用上下界 |
| 路径题忘到叶子 | 根到叶题必须叶子判断 |
| 层序混层 | 固定 `size` |

## 一题多变体

```text
Maximum Depth
↓
Balanced Binary Tree
↓
Diameter of Binary Tree
```

```text
Path Sum
↓
Path Sum II
↓
Path Sum III
```

```text
Validate BST
↓
Kth Smallest
↓
BST LCA
```

## 面试速记

- 树 DFS：空节点出口。
- 求子树信息：后序。
- 求每层：BFS。
- BST：中序有序 / 上下界。
- LCA：左右子树各找一个。
