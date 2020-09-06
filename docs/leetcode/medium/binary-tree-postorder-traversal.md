# Binary Tree Postorder Traversal

## [Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal)

Given the `root` of a binary tree, return the _postorder_ traversal of its nodes' values.

**Follow up:** Recursive solution is trivial, could you do it iteratively?

**Example 1:** ![](https://assets.leetcode.com/uploads/2020/08/28/pre1.jpg)

```text

Input: root = [1,null,2,3]
Output: [3,2,1]
```

**Example 2:**

```text

Input: root = []
Output: []
```

**Example 3:**

```text

Input: root = [1]
Output: [1]
```

**Example 4:** ![](https://assets.leetcode.com/uploads/2020/08/28/pre3.jpg)

```text

Input: root = [1,2]
Output: [2,1]
```

**Example 5:** ![](https://assets.leetcode.com/uploads/2020/08/28/pre2.jpg)

```text

Input: root = [1,null,2]
Output: [2,1]
```

**Constraints:**

* The number of the nodes in the tree is in the range `[0, 100]`.
* `-100 <= Node.val <= 100`

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
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root)
    {
        vector<int> res;

        if(!root)
            return res;
        if(root->left)
        {
            vector<int> &&tres = postorderTraversal(root->left);
            res.insert(res.end(), tres.begin(), tres.end());
        }

        if(root->right)
        {
            vector<int> &&tres = postorderTraversal(root->right);
            res.insert(res.end(), tres.begin(), tres.end());
        }

        res.emplace_back(root->val);


        return res;
    }
};
```

