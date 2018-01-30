

## Algorithm

二叉树：





## Sorting 排序

看看排序算法是如何工作是很有趣的，但在实践中，你几乎不必提供你自己的排序例程。

基础排序：

- 插入排序
- 选择排序
- Shell排

快速排序：

- 快速排序
- 合并排序
- 堆排序

性能不好排序：

- 冒泡排序
- 慢排序

### Data Structure 数据结构

### Tree
- Tree. 树
- [Binary Tree. 二叉树](https://github.com/huanjulu/Algorithm/blob/master/Binary%20Tree/README.md)
- Binary Search Tree(BST). 二叉搜索树
- Red-Black Tree. 红黑树
- AVL Tree. avl树
- B Tree. B树

### Lists


### 二叉树相关
**性质与定义**：
- 二叉树是一种树形结构，其特点是每个结点至多只有两颗子树，并且二叉树的子树有左右之分：
- 非空二叉树叶子结点数等于度为2的结点的个数加1，即N0 = N2 + 1 ：
- 非空二叉树上第K层上至多有2^(k-1)个结点。 ：
- 高度为H的二叉树至多有2^H - 1个结点 ：
- 树的最大度为2：

树的高度：从所有叶节点开始数高度到根节点，其中的最大值；也就是从结点x向下到某个叶结点最长简单路径中边的条数。（从下往上数） 
树的深度：是从根节点往下数

**找出二叉树中两个节点最远的距离 （最远两个节点的距离）**：
- 情况之一是根结点有左右子树 ：
（既然是最远，两个节点肯定是位于根结点的左右，左右之分。 
两个节点肯定是叶子节点。 
两个节点肯定是位于各自当前子树（相对于根结点）最大深度）
- 情况之二是根结点只有一个子树 ：
（最远的距离就在根节点的其中一个子树上的两个叶子结点。）

距离最远的两点必然在以某个节点A为根的子树上，它们间的路径必然经过该子树的根节点A。 
因而，以任意一个节点B为根的子树，计算出经过该子树根节点B的最大距离，则所有最大距离的最大值就是所要求的二叉树的最大距离，即“树的直径”。 
而经过树的根节点的最大距离为：左子树的高度+右子树的高度+2（假设空节点的高度为-1），因而，原问题等同于“计算每个节点的左子树和右子树的高度和，取最大值”。

计算二叉树中两个节点最远的距离 (其实也就是求左子树的最大高度，到根节点(也就是加一)，然后求右子树的最大高度，到根节点（也就是加一），总结来说。就是根结点的左，右子树的最大高度 加2)

**求二叉树的深度**：

二叉树的深度：它等于左子树和右子树中的最大深度加 1 （有两个过程，求左子树的深度，(非整棵树的深度)，以及右子树的深度(非整棵树的深度)，然后，加上根结点(也就是加一)） 

**二叉树的遍历**：

所谓树的遍历，就是敖着某种次序访问树中的点，切每个点刚好访问一次。也就是说，按照被访问的次序，可以得到一个某树节点所组成的一个序列。

一般来说，二叉树的广度优先我们指的一般是层序遍历。二叉树的深度遍历则是其余三种遍历方式

![](https://upload.wikimedia.org/wikipedia/commons/8/8a/%E5%89%8D%E5%BA%8F%E9%81%8D%E5%8E%86.png)


- [前序遍历的递归实现]()：

``` python
public void preOrder(TreeNode<T> node) {
        if(node == null)
            return;
        print(node);
        preOrder(node.left);
        preOrder(node.right);
    }
```

- [前序遍历的非递归实现]()：

利用辅助栈结构实现
``` python
 protected static void iterativePreorder(Node p) {  
        Stack<Node> stack = new Stack<Node>();  
        if (p != null) {  
            stack.push(p);  
            while (!stack.empty()) {  
                p = stack.pop();  
                visit(p);  
                if (p.getRight() != null)  
                    stack.push(p.getRight());  
                if (p.getLeft() != null)  
                    stack.push(p.getLeft());  
            }  
        }  
    }  
  
```


![](https://upload.wikimedia.org/wikipedia/commons/c/c4/%E4%B8%AD%E5%BA%8F%E9%81%8D%E5%8E%86.png)
- [中序遍历的递归实现]()：

``` python
public void inOrder(TreeNode<T> node) {
    if(node == null)
        return ;
    inOrder(node.left);
    //print
    print(node);
    inOrder(node.right);
}
```

- [中序遍历的非递归实现]()：

![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7f/%E5%90%8E%E5%BA%8F%E9%81%8D%E5%8E%86.png/440px-%E5%90%8E%E5%BA%8F%E9%81%8D%E5%8E%86.png)
- [后序遍历的递归实现]()：

``` python
public void postOrder(TreeNode<T> node) {
    if(node == null)
        return ;
    postOrder(node.left);
    postOrder(node.right);
    //print
    print(node);
}
}
```

![](https://upload.wikimedia.org/wikipedia/commons/c/c0/%E5%B1%82%E6%AC%A1%E9%81%8D%E5%8E%86.png)
- [层序遍历的非递归实现]()：




### 二叉搜索树相关 (Binary Search Tree)

**判断一颗二叉树你不是一个二叉搜索树**：

首先弄明白二叉搜索树的性质。 对于一颗二叉搜索树，左节点树值小于根结点，右节点数值大于根结点。
也就是说，对一颗bst来说，以中序遍历一边所组成的序列是一组递增的序列。
实现方式一。
``` python
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






-------------------
 [线性表](https://zh.wikipedia.org/wiki/Markdown)
 [栈与队列](https://zh.wikipedia.org/wiki/Markdown)
