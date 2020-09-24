## [Duplicate Zeros](https://leetcode.com/problems/duplicate-zeros)

<p>Given a fixed length&nbsp;array <code>arr</code> of integers, duplicate each occurrence of zero, shifting the remaining elements to the right.</p>

<p>Note that elements beyond the length of the original array are not written.</p>

<p>Do the above modifications to the input array <strong>in place</strong>, do not return anything from your function.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[1,0,2,3,0,4,5,0]</span>
<strong>Output: </strong>null
<strong>Explanation: </strong>After calling your function, the <strong>input</strong> array is modified to: <span id="example-output-1">[1,0,0,2,3,0,0,4]</span>
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[1,2,3]</span>
<strong>Output: </strong>null
<strong>Explanation: </strong>After calling your function, the <strong>input</strong> array is modified to: <span id="example-output-2">[1,2,3]</span>
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li><code>1 &lt;= arr.length &lt;= 10000</code></li>
	<li><code>0 &lt;= arr[i] &lt;= 9</code></li>
</ol>

## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
    template<typename T>
    void insert_stable_size(size_t pos, T val, vector<T> &arr)
    {
        for(size_t i = pos; i < arr.size(); ++i)
        {
            std::swap(val, arr[i]);
        }
    }
public:
    void duplicateZeros(vector<int>& arr)
    {
        //I am not using insert + pop_back
        //because the goal if the task is to do it manually
        for(size_t i = 0; i < arr.size()-1; ++i)
        {
            if(arr[i] == 0)
            {
                insert_stable_size(i+1, 0, arr);
                //skip inserted 0
                ++i;
            }
        }
    }
};
```
