## [Recover Binary Search Tree](https://leetcode.com/problems/recover-binary-search-tree)

<p>You are given the <code>root</code> of a binary search tree (BST), where exactly two nodes of the tree were swapped by mistake. <em>Recover the tree without changing its structure</em>.</p>

<p><strong>Follow up:</strong> A solution using <code>O(n)</code> space is pretty straight forward. Could you devise a constant space solution?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/28/recover1.jpg" style="width: 422px; height: 302px;" />
<pre>
<strong>Input:</strong> root = [1,3,null,null,2]
<strong>Output:</strong> [3,1,null,null,2]
<strong>Explanation:</strong> 3 cannot be a left child of 1 because 3 &gt; 1. Swapping 1 and 3 makes the BST valid.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/28/recover2.jpg" style="width: 581px; height: 302px;" />
<pre>
<strong>Input:</strong> root = [3,1,4,null,null,2]
<strong>Output:</strong> [2,1,4,null,null,3]
<strong>Explanation:</strong> 2 cannot be in the right subtree of 3 because 2 &lt; 3. Swapping 2 and 3 makes the BST valid.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[2, 1000]</code>.</li>
	<li><code>-2<sup>31</sup> &lt;= Node.val &lt;= 2<sup>31</sup> - 1</code></li>
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
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution
{
    TreeNode* find_X_then_value(TreeNode *root, int val, function<bool(int,int)> X)
    {
        if(!root)
            return nullptr;
        
        int val_to_check = val;
        if(X(root->val, val))
            val_to_check = root->val;

        
        TreeNode *res_left = find_X_then_value(root->left, val_to_check, X),
                 *res_right = find_X_then_value(root->right, val_to_check, X);
               
        if(res_left && res_right)
            return X(res_left->val, res_right->val) ? res_left :res_right;
        else if(res_left)
            return res_left;
        else if(res_right)
           return res_right; 
        else if(X(root->val, val))
            return root;
        

        return nullptr;

    }
    
public:
    void recoverTree(TreeNode* root)
    {
        if(!root)
            return;
        
        TreeNode *misplaced_left = find_X_then_value(root->left, root->val, std::greater<int>()),
                 *misplaced_right =  find_X_then_value(root->right, root->val, std::less<int>());
        
        if(misplaced_left && misplaced_right)
            std::swap(misplaced_left->val, misplaced_right->val);
        else if(misplaced_left)
            std::swap(root->val, misplaced_left->val);
        else if(misplaced_right)
            std::swap(root->val, misplaced_right->val);
        else
        {
            recoverTree(root->left);
            recoverTree(root->right);
        }
        
    }
};
```
