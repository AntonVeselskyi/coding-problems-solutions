# Binary Tree Inorder Traversal

## [Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal)

Given a binary tree, return the _inorder_ traversal of its nodes' values.

**Example:**

```text

Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [1,3,2]
```

**Follow up:** Recursive solution is trivial, could you do it iteratively?

## Solutions

### 🧠 Cpp

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode
 {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution
{
public:
    vector<int> inorderTraversal(TreeNode* root)
    {
        vector<int> res;

        if(!root)
            return res;
        if(root->left)
        {
            vector<int> &&tres = inorderTraversal(root->left);
            res.insert(res.end(), tres.begin(), tres.end());
        }

        res.emplace_back(root->val);

        if(root->right)
        {
            vector<int> &&tres = inorderTraversal(root->right);
            res.insert(res.end(), tres.begin(), tres.end());
        }

        return res;
    }
};
```

