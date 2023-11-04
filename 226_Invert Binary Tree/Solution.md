# Intuition
We must invert the binary tree in this question. Thus, we employ Post Order Treversal, whereby we go via the Left subtree, Right subtree, and finally return to the Parent node. We switch the Left and Right subtrees of the parent node when we return.
# Code
```
class Solution
{
public:
    TreeNode *invertTree(TreeNode *root)
    {
        if (root)
        {
            TreeNode *temp = root->left;
            root->left = root->right;
            root->right = temp;
            invertTree(root->left);
            invertTree(root->right);
        }
        return root;
    }
};
```
