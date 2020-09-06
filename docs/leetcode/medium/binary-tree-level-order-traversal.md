# Binary Tree Level Order Traversal

## [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal)

Given a binary tree, return the level order traversal of its nodes' values. \(ie, from left to right, level by level\).

 For example:  
 Given binary tree `[3,9,20,null,null,15,7]`,  


```text

    3
   / \
  9  20
    /  \
   15   7
```

 return its level order traversal as:  


```text

[
  [3],
  [9,20],
  [15,7]
]
```

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

#include <queue>
#include <utility>

class Solution
{

public:
    vector<vector<int>> levelOrder(TreeNode* root)
    {
        if(!root)
            return {};

        vector<vector<int>> res{};
        std::queue<TreeNode* >   q_to_process;
        q_to_process.push(root);

        do
        {
            //capture of this level values
            vector<int> level;
            //list of next level node to process on the next iteration
            std::queue<TreeNode*> q_next;

            for(TreeNode* node = q_to_process.front() ; !q_to_process.empty(); node = q_to_process.front())
            {
                q_to_process.pop();

                level.push_back(node->val);
                if(node->left)
                    q_next.push(node->left);
                if(node->right)
                    q_next.push(node->right);
            }

            res.push_back(std::move(level));
            q_to_process = std::move(q_next);

        }while(!q_to_process.empty());

        return res;
    }
};
```

