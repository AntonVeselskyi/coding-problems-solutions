## [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray)

<p>Given an integer array&nbsp;<code>nums</code>, find the contiguous subarray within an array (containing at least one number) which has the largest product.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [2,3,-2,4]
<strong>Output:</strong> <code>6</code>
<strong>Explanation:</strong>&nbsp;[2,3] has the largest product 6.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [-2,0,-1]
<strong>Output:</strong> 0
<strong>Explanation:</strong>&nbsp;The result cannot be 2, because [-2,-1] is not a subarray.</pre>


## Solutions
#### 🧠 Cpp
```cpp
#include <functional>
class Solution
{
public:
    int maxProduct(vector<int>& nums)
    {
        //case for 1 number
        if(nums.size() == 1)
            return nums[0];

        //erase consecutive 1 an -1
        bool removed_ones = true;
        if(nums.size() > 50)
        while(removed_ones)
        {
            removed_ones = false;
            for(auto iter = nums.begin()++; iter != nums.end()-2;)
            {
                int val = *iter;
                if(
                    (val == 1 || val == -1) &&
                        val == *next(iter)  ||
                    (val == 1 || val == -1) && 
                        (*next(iter) == val*-1 && *prev(iter) ==  val*-1 ) )             
                {
                    iter = nums.erase(iter);
                    removed_ones = true;
                }
                else
                   ++iter;

            }
        }

        int max = 0;
        for(auto begin_iter = nums.begin(); begin_iter < nums.end(); ++begin_iter)
        {
            int product = *begin_iter,
                new_product = *begin_iter;
           
            for(auto current_iter = next(begin_iter);
                current_iter < nums.end();
                current_iter++)
            {
                new_product *= *current_iter;
                if(new_product > product)
                    product = new_product;
            }
            
            if(product > max) max = product;
        }
        
        return max;
    }
};
```
