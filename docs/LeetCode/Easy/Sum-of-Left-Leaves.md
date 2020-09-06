## [Sum of Left Leaves](https://leetcode.com/problems/sum-of-left-leaves)

<p>Find the sum of all left leaves in a given binary tree.</p>

<p><b>Example:</b>
<pre>
    3
   / \
  9  20
    /  \
   15   7

There are two left leaves in the binary tree, with values <b>9</b> and <b>15</b> respectively. Return <b>24</b>.
</pre>
</p>

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
    enum Leaf{R, L};
public:
    int sumOfLeftLeaves(TreeNode* node, Leaf pos = R)
    {
        if(!node)
            return 0;
        
        if(pos == L && !node->right && !node->left)
            return node->val;
        
        return sumOfLeftLeaves(node->right, R) + sumOfLeftLeaves(node->left, L);
    }
};
```
