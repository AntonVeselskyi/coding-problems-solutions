## [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists)

<p>Merge two sorted linked lists and return it as a <strong>sorted</strong> list. The list should be made by splicing together the nodes of the first two lists.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/03/merge_ex1.jpg" style="width: 662px; height: 302px;" />
<pre>
<strong>Input:</strong> l1 = [1,2,4], l2 = [1,3,4]
<strong>Output:</strong> [1,1,2,3,4,4]
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> l1 = [], l2 = []
<strong>Output:</strong> []
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> l1 = [], l2 = [0]
<strong>Output:</strong> [0]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in both lists is in the range <code>[0, 50]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
	<li>Both <code>l1</code> and <code>l2</code> are sorted in <strong>non-decreasing</strong> order.</li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution
{
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2)
    {
        //input validation
        if(!l1 && !l2)
            return nullptr;
        if(!l1)
            return l2;
        if(!l2)
            return l1;
        
        //init of vars
        ListNode *&min_val_node = l1->val < l2->val ? l1 : l2;
        const int start_val = min_val_node->val;
        min_val_node = min_val_node->next;
        
        ListNode *new_list_start = new ListNode(start_val),
                 *new_list_iter = new_list_start;
        
        //O(n) solution, two pointers
        //while we have somthing in lists - merge them
        while(l1 || l2)
        {
            if(l2 == nullptr || (l1 && l1->val < l2->val)) 
            {
                new_list_iter->next = new ListNode(l1->val);
                new_list_iter = new_list_iter->next;
                l1 = l1->next;
            }
            else
            {
                new_list_iter->next = new ListNode(l2->val);
                new_list_iter = new_list_iter->next;
                l2 = l2->next;
            }
        }
        
        return new_list_start;
    }
};
```
