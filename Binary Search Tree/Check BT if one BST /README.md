


### 二叉搜索树相关 (Binary Search Tree)

**判断一颗二叉树是不是一个二叉搜索树**：

首先弄明白二叉搜索树的性质。 对于一颗二叉搜索树，左节点树值小于根结点，右节点数值大于根结点。
也就是说，对一颗bst来说，以中序遍历一边所组成的序列是一组递增的序列。
实现方式一。
``` java
public boolean isValid(Node root) {
     return isValidBST(root, Integer.MIN_VALUE,
          Integer.MAX_VALUE);
}
private boolean isValidBST(Node node, int l, int h) {
     if(node == null)
         return true;
     return node.value > l 
         && node.value < h
         && isValidBST(node.left, l, node.value)
         && isValidBST(node.right, node.value, h);
}
```
