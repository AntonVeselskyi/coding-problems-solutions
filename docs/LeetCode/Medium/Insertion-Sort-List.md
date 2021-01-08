## [Insertion Sort List](https://leetcode.com/problems/insertion-sort-list)

<p>Sort a linked list using insertion sort.</p>

<ol>
</ol>

<p><img alt="" src="https://upload.wikimedia.org/wikipedia/commons/0/0f/Insertion-sort-example-300px.gif" style="height:180px; width:300px" /><br />
<small>A graphical example of insertion sort. The partial sorted list (black) initially contains only the first element in the list.<br />
With each iteration one element (red) is removed from the input data and inserted in-place into the sorted list</small><br />
&nbsp;</p>

<ol>
</ol>

<p><strong>Algorithm of Insertion Sort:</strong></p>

<ol>
	<li>Insertion sort iterates, consuming one input element each repetition, and growing a sorted output list.</li>
	<li>At each iteration, insertion sort removes one element from the input data, finds the location it belongs within the sorted list, and inserts it there.</li>
	<li>It repeats until no input elements remain.</li>
</ol>

<p><br />
<strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 4-&gt;2-&gt;1-&gt;3
<strong>Output:</strong> 1-&gt;2-&gt;3-&gt;4
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> -1-&gt;5-&gt;3-&gt;4-&gt;0
<strong>Output:</strong> -1-&gt;0-&gt;3-&gt;4-&gt;5
</pre>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
    ListNode* insert(ListNode *root, int val)
    {
        ListNode *new_node = new ListNode(val),
                 *head = root;
        if(head->val > val)
        {
            new_node->next = head;
            return new_node;
        }
        
        while(head->next != nullptr && head->next->val < val)
            head = head->next;
        
        ListNode *tmp = head->next;
        head->next = new_node;
        new_node->next = tmp;
        
        return root;
    }
    
public:
    ListNode* insertionSortList(ListNode *head)
    {
        if(!head || !head->next)
            return head;
        
        //allocate sorted list
        ListNode *new_root =  new ListNode(head->val);
        
        for(ListNode *elem = head->next; elem; elem = elem->next)
        {
            new_root = insert(new_root, elem->val);
        }
        
        return new_root;
    }
};
```
