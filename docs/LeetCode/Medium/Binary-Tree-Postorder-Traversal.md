## [Binary Tree Postorder Traversal](https://leetcode.com/problems/binary-tree-postorder-traversal)

<p>Given the <code>root</code> of a&nbsp;binary tree, return the <em>postorder</em> traversal of its nodes&#39; values.</p>

<p><strong>Follow up:</strong> Recursive solution is trivial, could you do it iteratively?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/28/pre1.jpg" style="width: 202px; height: 317px;" />
<pre>
<strong>Input:</strong> root = [1,null,2,3]
<strong>Output:</strong> [3,2,1]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> root = []
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> root = [1]
<strong>Output:</strong> [1]
</pre>

<p><strong>Example 4:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/28/pre3.jpg" style="width: 202px; height: 197px;" />
<pre>
<strong>Input:</strong> root = [1,2]
<strong>Output:</strong> [2,1]
</pre>

<p><strong>Example 5:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/28/pre2.jpg" style="width: 202px; height: 197px;" />
<pre>
<strong>Input:</strong> root = [1,null,2]
<strong>Output:</strong> [2,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of the nodes in the tree is in the range <code>[0, 100]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
</ul>


## Solutions
#### 🧠 Cpp
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