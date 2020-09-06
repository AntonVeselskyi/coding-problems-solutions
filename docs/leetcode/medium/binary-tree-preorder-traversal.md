# Binary Tree Preorder Traversal

## [Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal)

Given a binary tree, return the _preorder_ traversal of its nodes' values.

**Example:**

```text

Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [1,2,3]
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
    vector<int> preorderTraversal(TreeNode* root)
    {
        vector<int> res;

        if(root)
            res.emplace_back(root->val);
        else
            return res;
        if(root->left)
        {
            vector<int> &&lres = preorderTraversal(root->left);
            res.insert(res.end(), lres.begin(), lres.end());
        }
        if(root->right)
        {
            vector<int> &&lres = preorderTraversal(root->right);
            res.insert(res.end(), lres.begin(), lres.end());
        }
        return res;
    }
};
```

