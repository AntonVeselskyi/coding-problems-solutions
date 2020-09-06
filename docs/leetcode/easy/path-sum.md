# Path Sum

## [Path Sum](https://leetcode.com/problems/path-sum)

Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

**Note:** A leaf is a node with no children.

**Example:**

Given the below binary tree and `sum = 22`,

```text

      5
     / \
    4   8
   /   / \
  11  13  4
 /  \      \
7    2      1
```

return true, as there exist a root-to-leaf path `5->4->11->2` which sum is 22.

## Solutions

### 🧠 Cpp

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */

//using preorder traversal (passing info to the children)
//each child
class Solution {
public:
    bool hasPathSum(TreeNode* root, int sum)
    {
        if (!root)
            return false;

        //if leaf return specific value
        if(!root->left && !root->right)
            //if it has value that fulfill the request
            return root->val-sum == 0;
        else //has more leafs
            return hasPathSum(root->left, sum - root->val)
                   || hasPathSum(root->right, sum - root->val);
    }
};
```

