#  Path Sum
## 问题分析：
递归求解,以及调用左右子树。
## 编程实现：
```C++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool hasPathSum(TreeNode* root, int sum) {    
        if(root==NULL) return false;       
        if(root->left==NULL && root->right==NULL && sum-root->val==0)           
               return true;        
        return hasPathSum(root->left,sum-root->val) || hasPathSum(root->right,sum-root->val);
    }
};
```

# Balanced Binary Tree
## 问题分析：
平衡二叉树,是一 棵空树或它的左右两个子树的高度差的绝对值不超过1
## 编程实现：
```C++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isBalanced(TreeNode* root) {
        return depth(root) != -1;
    }
    int depth(TreeNode *root)
    {
        if (root==NULL)
            return 0;
        int left=depth(root->left);
        int right=depth(root->right);
        if(left==-1||right==-1||abs(left-right) > 1)
            return -1;
        return max(left,right) + 1;
    }
};
```
