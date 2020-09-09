## [All Elements in Two Binary Search Trees](https://leetcode.com/problems/all-elements-in-two-binary-search-trees)

<p>Given two binary search trees <code>root1</code> and <code>root2</code>.</p>

<p>Return a list containing <em>all the integers</em> from <em>both trees</em> sorted in <strong>ascending</strong> order.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/12/18/q2-e1.png" style="width: 457px; height: 207px;" />
<pre>
<strong>Input:</strong> root1 = [2,1,4], root2 = [1,0,3]
<strong>Output:</strong> [0,1,1,2,3,4]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> root1 = [0,-10,10], root2 = [5,1,7,0,2]
<strong>Output:</strong> [-10,0,0,1,2,5,7,10]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> root1 = [], root2 = [5,1,7,0,2]
<strong>Output:</strong> [0,1,2,5,7]
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> root1 = [0,-10,10], root2 = []
<strong>Output:</strong> [-10,0,10]
</pre>

<p><strong>Example 5:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/12/18/q2-e5-.png" style="width: 352px; height: 197px;" />
<pre>
<strong>Input:</strong> root1 = [1,null,8], root2 = [8,1]
<strong>Output:</strong> [1,1,8,8]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>Each tree has at most <code>5000</code> nodes.</li>
	<li>Each node&#39;s value is between <code>[-10^5, 10^5]</code>.</li>
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
    void insert_node(TreeNode *&root, int val)
    {
        if(!root) 
            root = new TreeNode(val);
        else if(val < root->val)
        {
            if(root->left)
                insert_node(root->left, val);
            else
                root->left = new TreeNode(val);
        }
        else
        {
            if(root->right)
                insert_node(root->right, val);
            else
                root->right = new TreeNode(val);
        }
    }
    
    void for_each_node(TreeNode *root, std::function<void(int)> func)
    {
        if(!root) return;
        
        for_each_node(root->left, func);
        func(root->val);
        for_each_node(root->right, func);  
    }
    

public:
    vector<int> getAllElements(TreeNode *root1, TreeNode *root2)
    {
        for_each_node(root2, [&root1, this](int val){ this->insert_node(root1, val); } );
        
        vector<int> res;
        for_each_node(root1, [&res](int val){ res.push_back(val); });
        return res;
        
    }
        
};
```
