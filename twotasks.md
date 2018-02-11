# Same Tree
## 问题分析：
二叉树的遍历问题,这里使用迭代的方法,同时遍历两个数,将每个节点进行比较，
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
    bool isSameTree(TreeNode* p, TreeNode* q) {
        class Solution {
        stack<TreeNode*> s1, s2;
        if (p) s1.push(p);
        if (q) s2.push(q);
        while (!s1.empty() && !s2.empty()) {
            TreeNode *t1 = s1.top(); s1.pop();
            TreeNode *t2 = s2.top(); s2.pop();
            if (t1->val != t2->val) return false;
            if (t1->left) s1.push(t1->left);
            if (t2->left) s2.push(t2->left);
            if (s1.size() != s2.size()) return false;
            if (t1->right) s1.push(t1->right);
            if (t2->right) s2.push(t2->right);
            if (s1.size() != s2.size()) return false;
        }
        return s1.size() == s2.size();
    }
};
```


# Symmetric Tree
## 问题分析：
判断二叉树是否对称,有两个节点n1, n2,需比较n1的左子节点的值和n2的右子节点的值是否相等,
同时还要比较n1的右子节点的值和n2的左子结点的值是否相等,类推比较完所有左右节点。
## 编程实现：
```C++
/**
 * Definition for binary tree
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSymmetric(TreeNode *root) {
        if (!root) return true;
        return isSymmetric(root->left, root->right);
    }
    bool isSymmetric(TreeNode *left, TreeNode *right) {
        if (!left && !right) return true;
        if (left && !right || !left && right || left->val != right->val) return false;
        return isSymmetric(left->left, right->right) && isSymmetric(left->right, right->left);
    }
    
};
```
