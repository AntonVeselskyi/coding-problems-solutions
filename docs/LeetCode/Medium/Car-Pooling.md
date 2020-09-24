## [Car Pooling](https://leetcode.com/problems/car-pooling)

<p>You are driving a vehicle that&nbsp;has <code>capacity</code> empty seats initially available for passengers.&nbsp; The vehicle <strong>only</strong> drives east (ie. it <strong>cannot</strong> turn around and drive west.)</p>

<p>Given a list of <code>trips</code>, <code>trip[i] = [num_passengers, start_location, end_location]</code>&nbsp;contains information about the <code>i</code>-th trip: the number of passengers that must be picked up, and the locations to pick them up and drop them off.&nbsp; The locations are given as the number of kilometers&nbsp;due east from your vehicle&#39;s initial location.</p>

<p>Return <code>true</code> if and only if&nbsp;it is possible to pick up and drop off all passengers for all the given trips.&nbsp;</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>trips = <span id="example-input-1-1">[[2,1,5],[3,3,7]]</span>, capacity = <span id="example-input-1-2">4</span>
<strong>Output: </strong><span id="example-output-1">false</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>trips = <span id="example-input-2-1">[[2,1,5],[3,3,7]]</span>, capacity = <span id="example-input-2-2">5</span>
<strong>Output: </strong><span id="example-output-2">true</span>
</pre>

<div>
<p><strong>Example 3:</strong></p>

<pre>
<strong>Input: </strong>trips = <span id="example-input-3-1">[[2,1,5],[3,5,7]]</span>, capacity = <span id="example-input-3-2">3</span>
<strong>Output: </strong><span id="example-output-3">true</span>
</pre>

<div>
<p><strong>Example 4:</strong></p>

<pre>
<strong>Input: </strong>trips = <span id="example-input-4-1">[[3,2,7],[3,7,9],[8,3,9]]</span>, capacity = <span id="example-input-4-2">11</span>
<strong>Output: </strong><span id="example-output-4">true</span>
</pre>
</div>
</div>
</div>

<div>
<div>
<div>
<div>&nbsp;</div>
</div>
</div>
</div>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ol>
	<li><code>trips.length &lt;= 1000</code></li>
	<li><code>trips[i].length == 3</code></li>
	<li><code>1 &lt;= trips[i][0] &lt;= 100</code></li>
	<li><code>0 &lt;= trips[i][1] &lt; trips[i][2] &lt;= 1000</code></li>
	<li><code>1 &lt;=&nbsp;capacity &lt;= 100000</code></li>
</ol>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
    enum
    {
        NUM_PASS,
        START,
        END
    };

public:
    bool carPooling(vector<vector<int>> trips, int capacity)
    {
        //sort by starting point
        std::sort(begin(trips), end(trips),
                 [](auto a, auto b)
                 {
                     return a[START] < b[START];
                 });
        
        
        list<vector<int>*> bus;
        size_t passenger_num = 0;
        for(auto &trip : trips)
        {
            for(auto *&passenger : bus)
            {
                if(!passenger)
                    continue;

                //get off the bus unneeded passengers
                if((*passenger)[END] <= trip[START])
                {
                    passenger_num -= (*passenger)[NUM_PASS];
                    passenger = nullptr;
                }
            }
            
            if(passenger_num + trip[NUM_PASS] <= capacity)
            {
                bus.push_back(&trip);
                passenger_num += trip[NUM_PASS];
            }
            else
                return false;
        }
        
        return true;   
    }
};
```
