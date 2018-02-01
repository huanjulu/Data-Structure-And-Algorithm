**二叉树的遍历**：

所谓树的遍历，就是按照着某种次序访问树中的点，切每个点刚好访问一次。也就是说，按照被访问的次序，可以得到一个某树节点所组成的一个序列。

一般来说，二叉树的广度优先我们指的一般是层序遍历。二叉树的深度遍历则是其余三种遍历方式


### 前序遍历实现方式

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

