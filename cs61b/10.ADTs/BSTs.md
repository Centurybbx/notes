# BSTs(Binary Search Trees)

- **前言**

​	对于Linked List, 其查找性能会根据不同的情况而发生变化，当需要查找的元素在链表的末端时它需要一个线性的时间，基于这种场景，我们进行学习BST，它的查找时间是log~2~(n)。

​	如果我们将二分查找应用到链表中，那么就形成了一个二叉树。

## Properties of trees

树的组成：

- 结点
- 连接结点的边
  - **约束**：两个结点之间只能有一个通路

**根结点**：没有父母结点的结点

**叶子结点**：没有孩子结点的结点

---

对树更精细的定义划分：

- Binary Trees: 除了上述的条件之外，每个结点都有0/1/2个子结点。
- Binary Search Trees: 除了上述的条件之外，每个结点X还要有以下属性：
  - X的左子树的值都小于X的值。
  - X的右子树的值都大于X的值。

```java
private class BST<Key> {
    private Key key;
    private BST left;
    private BST right;

    public BST(Key key, BST left, BST Right) {
        this.key = key;
        this.left = left;
        this.right = right;
    }

    public BST(Key key) {
        this.key = key;
    }
```

## Binary Search Tree Operations

### Search

​	对于BST来说，其查找方式与Binary Search基本一样，都是从中间位置(根节点)来找。小于其值的往左找，大于的往右找，如果找到就返回，找不到就null。