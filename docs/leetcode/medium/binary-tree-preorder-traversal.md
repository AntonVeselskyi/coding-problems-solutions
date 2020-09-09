## [Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal)

<p>Given a binary tree, return the <em>preorder</em> traversal of its nodes&#39; values.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>&nbsp;<code>[1,null,2,3]</code>
   1
    \
     2
    /
   3

<strong>Output:</strong>&nbsp;<code>[1,2,3]</code>
</pre>

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
