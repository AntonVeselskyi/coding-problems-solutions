# Lowest Common Ancestor of a Binary Tree

## [Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree)

Given a binary tree, find the lowest common ancestor \(LCA\) of two given nodes in the tree.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants \(where we allow **a node to be a descendant of itself**\).”

Given the following binary tree:  root = \[3,5,1,6,2,0,8,null,null,7,4\] ![](https://assets.leetcode.com/uploads/2018/12/14/binarytree.png)

**Example 1:**

```text

Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
Output: 3
Explanation: The LCA of nodes 5 and 1 is 3.
```

**Example 2:**

```text

Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
Output: 5
Explanation: The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.
```

**Note:**

* All of the nodes' values will be unique.
* p and q are different and both values will exist in the binary tree.

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

