

** Find Minimum Depth of a Binary Tree

给出一颗二叉树，找出其最小的深度。最小的深度计算是，根结点到最近的叶子节点的最短路径节点的数量 。

例如，下图二叉树最小深度是2


![GitHub](https://github.com/huanjulu/Data-Structure-And-Algorithm/blob/master/Binary%20Tree/Calculate%20Minmum%20Depth%20Of%20Tree%20copy/tree122.gif)

Note that the path must end on a leaf node, For example, minimum depth of below Binary Tree is also 2

这个算法的细想是遍历一颗二叉树, 对于二叉树中的每一个节点, 检查该节点是否是一个leaf node(方法是该节点的左右子节点为null). 如果是叶子节点, 那么就返回1. 如果不是叶子节点, 且它的左子树为null, 则计算该节点的右子树节点。 如果右子树为null, 则计算该节点的左子树节点。如果左子树以及右子树同时为null, 则取他们中较小的一个并返回。



``` java
  int minimumDepth(Node root)
    {
        // Corner case. Should never be hit unless the code is
        // called on root = NULL
        if (root == null)
            return 0;
 
        // Base case : Leaf Node. This accounts for height = 1.
        if (root.left == null && root.right == null)
            return 1;
 
        // If left subtree is NULL, recur for right subtree
        if (root.left == null)
            return minimumDepth(root.right) + 1;
 
        // If right subtree is NULL, recur for right subtree
        if (root.right == null)
            return minimumDepth(root.left) + 1;
 
        return Math.min(minimumDepth(root.left),
                        minimumDepth(root.right)) + 1;
    }
 
```

