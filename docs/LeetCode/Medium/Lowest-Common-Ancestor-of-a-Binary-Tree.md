## [Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree)

<p>Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.</p>

<p>According to the <a href="https://en.wikipedia.org/wiki/Lowest_common_ancestor" target="_blank">definition of LCA on Wikipedia</a>: &ldquo;The lowest common ancestor is defined between two nodes p&nbsp;and q&nbsp;as the lowest node in T that has both p&nbsp;and q&nbsp;as descendants (where we allow <b>a node to be a descendant of itself</b>).&rdquo;</p>

<p>Given the following binary tree:&nbsp; root =&nbsp;[3,5,1,6,2,0,8,null,null,7,4]</p>
<img alt="" src="https://assets.leetcode.com/uploads/2018/12/14/binarytree.png" style="width: 200px; height: 190px;" />
<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
<strong>Output:</strong> 3
<strong>Explanation: </strong>The LCA of nodes <code>5</code> and <code>1</code> is <code>3.</code>
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
<strong>Output:</strong> 5
<strong>Explanation: </strong>The LCA of nodes <code>5</code> and <code>4</code> is <code>5</code>, since a node can be a descendant of itself according to the LCA definition.
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ul>
	<li>All of the nodes&#39; values will be unique.</li>
	<li>p and q are different and both values will&nbsp;exist in the binary tree.</li>
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
    
    bool has_element(TreeNode* el, TreeNode* p)
    {
        if(el == nullptr)
            return false;
        if(el == p)
            return true;
        else
            return has_element(el->right, p) || has_element(el->left, p);
    }
    

    
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q)
    {
        if(!root) 
            return nullptr;

        if (has_element(root, p) && has_element(root, q))
        {
            if(has_element(root->right, p) && has_element(root->right, q))
                return lowestCommonAncestor(root->right, p, q);
            else if(has_element(root->left, p) && has_element(root->left, q))
                return lowestCommonAncestor(root->left, p, q);
            else return root;
        }
        else
            return nullptr;
                
    }
};
```