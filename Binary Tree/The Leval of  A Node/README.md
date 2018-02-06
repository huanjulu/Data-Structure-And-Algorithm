

** Get Level of a node in a Binary Tree

Given a Binary Tree and a key, write a function that returns level of the key.

例如, 思考下图一颗二叉树, 如果输入一个数值k=3, 然后程序应该返回1. 如果输入的数值为4， 然后程序方法返回的数值为3. 如果输入的数值在二叉树中不存在，则应该返回0 


![GitHub](https://github.com/huanjulu/Data-Structure-And-Algorithm/blob/master/Binary%20Tree/The%20Leval%20of%20%20A%20Node/tree_bst.gif)

从根节点开始, 并且根结点的层数作为1. 如果输入的数据匹配根结点，返回层数1，否则遍历左右子树，level + 1


``` java
 int getLevelUtil(Node node, int data, int level) 
    {
        if (node == null)
            return 0;
  
        if (node.data == data)
            return level;
  
        int downlevel = getLevelUtil(node.left, data, level + 1);
        if (downlevel != 0)
            return downlevel;
  
        downlevel = getLevelUtil(node.right, data, level + 1);
        return downlevel;
    }
  
    /* Returns level of given data value */
    int getLevel(Node node, int data) 
    {
        return getLevelUtil(node, data, 1);
    }
```

  
  
