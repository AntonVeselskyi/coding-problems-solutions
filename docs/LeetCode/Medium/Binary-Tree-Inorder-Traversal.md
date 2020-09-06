## [Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal)

<p>Given a binary tree, return the <em>inorder</em> traversal of its nodes&#39; values.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> [1,null,2,3]
   1
    \
     2
    /
   3

<strong>Output:</strong> [1,3,2]</pre>

<p><strong>Follow up:</strong> Recursive solution is trivial, could you do it iteratively?</p>


## Solutions
#### 🧠 Cpp
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
