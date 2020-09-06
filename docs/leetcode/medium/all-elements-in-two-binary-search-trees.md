# All Elements in Two Binary Search Trees

## [All Elements in Two Binary Search Trees](https://leetcode.com/problems/all-elements-in-two-binary-search-trees)

Given two binary search trees `root1` and `root2`.

Return a list containing _all the integers_ from _both trees_ sorted in **ascending** order.

**Example 1:** ![](https://assets.leetcode.com/uploads/2019/12/18/q2-e1.png)

```text

Input: root1 = [2,1,4], root2 = [1,0,3]
Output: [0,1,1,2,3,4]
```

**Example 2:**

```text

Input: root1 = [0,-10,10], root2 = [5,1,7,0,2]
Output: [-10,0,0,1,2,5,7,10]
```

**Example 3:**

```text

Input: root1 = [], root2 = [5,1,7,0,2]
Output: [0,1,2,5,7]
```

**Example 4:**

```text

Input: root1 = [0,-10,10], root2 = []
Output: [-10,0,10]
```

**Example 5:** ![](https://assets.leetcode.com/uploads/2019/12/18/q2-e5-.png)

```text

Input: root1 = [1,null,8], root2 = [8,1]
Output: [1,1,8,8]
```

**Constraints:**

* Each tree has at most `5000` nodes.
* Each node's value is between `[-10^5, 10^5]`.

## Solutions

### 🧠 Cpp

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

