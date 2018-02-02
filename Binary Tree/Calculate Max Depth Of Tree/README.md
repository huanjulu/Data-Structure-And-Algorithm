**求二叉树的最大深度**：

二叉树的思想大部分可以利用分治解决

二叉树的深度：它等于左子树和右子树中的最大深度加 1 （有两个过程，求左子树的深度，(非整棵树的深度)，以及右子树的深度(非整棵树的深度)，然后，加上根结点(也就是加一)） 


``` java
 public void findMaxmumDepthOfBinaryTree(TreeNode* root){
  if(root == NULL){
        return 0;
    }
    int depth_left = maxDepth(root->left) + 1;
    int depth_right = maxDepth(root->right) + 1;
    return depth_left > depth_right ? depth_left : depth_right;
}
```
