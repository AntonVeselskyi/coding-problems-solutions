## [Sum of Root To Leaf Binary Numbers](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers)

<p>You are given the <code>root</code> of a binary tree where each node has a value <code>0</code>&nbsp;or <code>1</code>.&nbsp; Each root-to-leaf path represents a binary number starting with the most significant bit.&nbsp; For example, if the path is <code>0 -&gt; 1 -&gt; 1 -&gt; 0 -&gt; 1</code>, then this could represent <code>01101</code> in binary, which is <code>13</code>.</p>

<p>For all leaves in the tree, consider the numbers represented by the path&nbsp;from the root to that leaf.</p>

<p>Return <em>the sum of these numbers</em>. The answer is <strong>guaranteed</strong> to fit in a <strong>32-bits</strong> integer.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2019/04/04/sum-of-root-to-leaf-binary-numbers.png" style="width: 450px; height: 296px;" />
<pre>
<strong>Input:</strong> root = [1,0,1,0,1,0,1]
<strong>Output:</strong> 22
<strong>Explanation: </strong>(100) + (101) + (110) + (111) = 4 + 5 + 6 + 7 = 22
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> root = [0]
<strong>Output:</strong> 0
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> root = [1]
<strong>Output:</strong> 1
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> root = [1,1]
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 1000]</code>.</li>
	<li><code>Node.val</code> is <code>0</code> or <code>1</code>.</li>
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
    //list of binary represented
    static list<list<int>> getAllNumbers(TreeNode* root)
    {
        if(!root)
            return {};
        //if leaf
        if(!root->left && !root->right)
            return list<list<int>>{{root->val}};
        
        list<list<int>> res;
        auto process_leaf = [&](TreeNode* leaf)
        {
            if(leaf)
            for(auto num : getAllNumbers(leaf))
            {
                num.push_front(root->val);
                res.push_back(num);
            }
        };
        
        process_leaf(root->left);
        process_leaf(root->right);
        
        return res;
    }

public:
    int sumRootToLeaf(TreeNode* root)
    {
        int res = 0;
        for(auto num : getAllNumbers(root))
        {
            string binary_string;
            for(int bit : num)
                binary_string.push_back(to_string(bit)[0]);
            res += std::stoi(binary_string, nullptr, 2);
        }
        return res;
    }
};
```
