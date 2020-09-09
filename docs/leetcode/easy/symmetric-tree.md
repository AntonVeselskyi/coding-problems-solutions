## [Symmetric Tree](https://leetcode.com/problems/symmetric-tree)

<p>Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).</p>

<p>For example, this binary tree <code>[1,2,2,3,4,4,3]</code> is symmetric:</p>

<pre>
    1
   / \
  2   2
 / \ / \
3  4 4  3
</pre>

<p>&nbsp;</p>

<p>But the following <code>[1,2,2,null,3,null,3]</code> is not:</p>

<pre>
    1
   / \
  2   2
   \   \
   3    3
</pre>

<p>&nbsp;</p>

<p><b>Follow up:</b> Solve it both recursively and iteratively.</p>


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

#include <utility>
class Solution
{
public:
    bool isSymmetric(TreeNode* root)
    {
        if(!root)
            return true;
        if( !!root->left != !!root->right)
            return false;
        if(!root->left)
            return true;

        //idea use level-traversal 
        //to check that left and right side has symetric leafs
        
        //we will check level by level
        //each level will have 2*n elements
        list<TreeNode*> level{root->left, root->right};
        
        while(!level.empty())
        {
            list<TreeNode*> next_level_left;
            list<TreeNode*> next_level_right;
            
            for(TreeNode *left_el=level.front(), *right_el =level.back();
                !level.empty();
                left_el=level.front(), right_el = level.back())
            {
                //check for symmetric form
                if( !!left_el->left == !!right_el->right && !!left_el->right == !!right_el->left
                //check for same content
                   && left_el->val == right_el->val )
                {
                    if(left_el->left)
                    {
                        next_level_left.emplace_back(left_el->left);
                        next_level_right.emplace_back(right_el->right);
                    }
                    if(left_el->right)
                    {
                        next_level_left.emplace_back(left_el->right);
                        next_level_right.emplace_back(right_el->left);
                    }
                    
                    level.pop_front();
                    level.pop_back();
                }
                else
                    return false;
            }
            
            reverse(next_level_right.begin(), next_level_right.end());
            level = std::move(next_level_left);
            level.insert(level.end(),
                         std::make_move_iterator(next_level_right.begin()),
                         std::make_move_iterator(next_level_right.end()));
             
            
        }
        
        return true;
        
        
    }
};
```
