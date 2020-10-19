## [Sort List](https://leetcode.com/problems/sort-list)

<p>Given the <code>head</code> of a linked list, return <em>the list after sorting it in <strong>ascending order</strong></em>.</p>

<p><strong>Follow up:</strong> Can you sort the linked list in <code>O(n logn)</code> time and <code>O(1)</code>&nbsp;memory (i.e. constant space)?</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/14/sort_list_1.jpg" style="width: 450px; height: 194px;" />
<pre>
<strong>Input:</strong> head = [4,2,1,3]
<strong>Output:</strong> [1,2,3,4]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/09/14/sort_list_2.jpg" style="width: 550px; height: 184px;" />
<pre>
<strong>Input:</strong> head = [-1,5,3,4,0]
<strong>Output:</strong> [-1,0,3,4,5]
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> head = []
<strong>Output:</strong> []
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the list is in the range <code>[0, 5 * 10<sup>4</sup>]</code>.</li>
	<li><code>-10<sup>5</sup> &lt;= Node.val &lt;= 10<sup>5</sup></code></li>
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
    //count sort with a lot of SPACE
    //but O(1) space and O(n) time
    ListNode* sortList(ListNode* head)
    {
        vector<size_t> minus_cout_table(100000);
        vector<size_t> plus_cout_table(100000);
        
        for(auto iter = head; iter; iter = iter->next)
        {
            if(iter->val < 0)
                minus_cout_table[abs(iter->val)]++;
            else
                plus_cout_table[iter->val]++;
        }
        
        ListNode *new_head = nullptr,
        *iter = nullptr;

        for(int i = minus_cout_table.size()-1; i >= 0; i--)
        {
            if(minus_cout_table[i])
            for(int j = 0; j < minus_cout_table[i]; j++)
            {

                ListNode* new_node = new ListNode(-1*i);
                if(!iter)
                {
                    new_head = new_node;
                    iter = new_head;
                }
                else
                {
                    iter->next = new_node;
                    iter = new_node;
                }
            }
        }

        for(int i = 0; i <  plus_cout_table.size(); i++)
        {
            if(plus_cout_table[i])
            for(int j = 0; j < plus_cout_table[i]; j++)
            {

                ListNode* new_node = new ListNode(i);
                if(!iter)
                {
                    new_head = new_node;
                    iter = new_head;
                }
                else
                {
                    iter->next = new_node;
                    iter = new_node;
                }
            }
        }
        
        return new_head;
    }
};
```
