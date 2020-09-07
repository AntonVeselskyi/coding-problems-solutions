## [Parsing A Boolean Expression](https://leetcode.com/problems/parsing-a-boolean-expression)

<p>Return the result of evaluating a given boolean <code>expression</code>, represented as a string.</p>

<p>An expression can either be:</p>

<ul>
	<li><code>&quot;t&quot;</code>, evaluating to <code>True</code>;</li>
	<li><code>&quot;f&quot;</code>, evaluating to <code>False</code>;</li>
	<li><code>&quot;!(expr)&quot;</code>, evaluating to the logical NOT of the inner expression <code>expr</code>;</li>
	<li><code>&quot;&amp;(expr1,expr2,...)&quot;</code>, evaluating to the logical AND of 2 or more inner expressions <code>expr1, expr2, ...</code>;</li>
	<li><code>&quot;|(expr1,expr2,...)&quot;</code>, evaluating to the logical OR of 2 or more inner expressions <code>expr1, expr2, ...</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> expression = &quot;!(f)&quot;
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> expression = &quot;|(f,t)&quot;
<strong>Output:</strong> true
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> expression = &quot;&amp;(t,f)&quot;
<strong>Output:</strong> false
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> expression = &quot;|(&amp;(t,f,t),!(t))&quot;
<strong>Output:</strong> false
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= expression.length &lt;= 20000</code></li>
	<li><code>expression[i]</code>&nbsp;consists of characters in <code>{&#39;(&#39;, &#39;)&#39;, &#39;&amp;&#39;, &#39;|&#39;, &#39;!&#39;, &#39;t&#39;, &#39;f&#39;, &#39;,&#39;}</code>.</li>
	<li><code>expression</code> is a valid expression representing a boolean, as given in the description.</li>
</ul>


## Solutions
#### 🧠 Cpp
```cpp
class Solution
{
    // IN: string with coma separated BOOL expressions
    // OUT: list of corresponding BOOL values
    list<bool> deduceBoolList(string exprs)
    {
        list<bool> res;

        const char *c_exprs = exprs.c_str();
        do
        {
            //if we are on coma. step over it
            if(*c_exprs == ',')
                c_exprs++;

            //if we have an operator with argumets
            if(c_exprs[1] == '(')
            {
                //to find the end, we must count every ()
                const char *exp_end = c_exprs+2;
                size_t active_parentheses_num = 1;
                while(active_parentheses_num)
                {
                    exp_end++;
                    if(*exp_end == '(')
                        active_parentheses_num++;
                    if(*exp_end == ')')
                        active_parentheses_num--;
                }
                
                //when end is found form string with whole expression
                string exp(c_exprs, exp_end-c_exprs+1);
                res.push_back(parseBoolExpr(exp));
                c_exprs = exp_end+1;
            }
            else
            {
                string exp(1,*c_exprs);
                res.push_back(parseBoolExpr(exp));
            }
                
        }
        while(c_exprs = strchr(c_exprs, ','));
        
        return res;
    }
    
    using fbbb = function<bool(bool,bool)>;

public:

    bool parseBoolExpr(string expression)
    {
        if(expression == "f")
            return false;
        if(expression == "t")
            return true;

         //3 chars: !()
        string in_parentheses = expression.substr(2, expression.size() - 3);

        //check for !
        if(expression.front() == '!')
            return !parseBoolExpr(in_parentheses); 


        //else we have & or |        
        list<bool> values = deduceBoolList(in_parentheses);
        auto operation = expression.front() == '&' ? 
                         (fbbb)bit_and<bool>() :
                          bit_or<bool>();

        return std::accumulate(values.begin(), values.end(), values.front(),
                               operation);

    }
};

```
