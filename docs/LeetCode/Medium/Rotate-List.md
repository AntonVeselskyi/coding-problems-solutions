## [Rotate List](https://leetcode.com/problems/rotate-list)

<p>Given a linked&nbsp;list, rotate the list to the right by <em>k</em> places, where <em>k</em> is non-negative.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL, k = 2
<strong>Output:</strong> 4-&gt;5-&gt;1-&gt;2-&gt;3-&gt;NULL
<strong>Explanation:</strong>
rotate 1 steps to the right: 5-&gt;1-&gt;2-&gt;3-&gt;4-&gt;NULL
rotate 2 steps to the right: 4-&gt;5-&gt;1-&gt;2-&gt;3-&gt;NULL
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 0-&gt;1-&gt;2-&gt;NULL, k = 4
<strong>Output:</strong> <code>2-&gt;0-&gt;1-&gt;NULL</code>
<strong>Explanation:</strong>
rotate 1 steps to the right: 2-&gt;0-&gt;1-&gt;NULL
rotate 2 steps to the right: 1-&gt;2-&gt;0-&gt;NULL
rotate 3 steps to the right:&nbsp;<code>0-&gt;1-&gt;2-&gt;NULL</code>
rotate 4 steps to the right:&nbsp;<code>2-&gt;0-&gt;1-&gt;NULL</code></pre>


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
