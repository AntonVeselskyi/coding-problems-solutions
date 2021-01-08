## [Rotate List](https://leetcode.com/problems/rotate-list)

<p>Given the <code>head</code> of a linked&nbsp;list, rotate the list to the right by <code>k</code> places.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/rotate1.jpg" style="width: 600px; height: 254px;" />
<pre>
<strong>Input:</strong> head = [1,2,3,4,5], k = 2
<strong>Output:</strong> [4,5,1,2,3]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/11/13/roate2.jpg" style="width: 472px; height: 542px;" />
<pre>
<strong>Input:</strong> head = [0,1,2], k = 4
<strong>Output:</strong> [2,0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the list is in the range <code>[0, 500]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
	<li><code>0 &lt;= k &lt;= 2 * 10<sup>9</sup></code></li>
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
    //O(n)solution with circular list
    ListNode* rotateRight(ListNode* head, int k)
    {
        if(!head)
            return head;
        
        //find list length and save tail
        size_t length = 0;
        ListNode *tail = nullptr;
        for(ListNode *counter = head; counter; ++length, counter = counter->next)
            if(!counter->next)
                tail = counter;
        
        //make list circular
        tail->next = head;
        
        //module k
        k = k % length;
        
        //we will move k last element to front
        //length - k element will be a new tail
        //length - k + 1 element will be a new head
        
        //find new tail:
        tail = head;
        for(int i = 0; i < length - k - 1; ++i, tail = tail->next);
        
        head = tail->next;
        tail->next = nullptr;
        
        return head;
    }
};
```
