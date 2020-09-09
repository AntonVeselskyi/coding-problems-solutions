## [Word Pattern](https://leetcode.com/problems/word-pattern)

<p>Given a <code>pattern</code> and a string <code>str</code>, find if <code>str</code> follows the same pattern.</p>

<p>Here <b>follow</b> means a full match, such that there is a bijection between a letter in <code>pattern</code> and a <b>non-empty</b> word in <code>str</code>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog cat cat dog&quot;</code>
<strong>Output:</strong> true</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong>pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog cat cat fish&quot;</code>
<strong>Output:</strong> false</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> pattern = <code>&quot;aaaa&quot;</code>, str = <code>&quot;dog cat cat dog&quot;</code>
<strong>Output:</strong> false</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog dog dog dog&quot;</code>
<strong>Output:</strong> false</pre>

<p><b>Notes:</b><br />
You may assume <code>pattern</code> contains only lowercase letters, and <code>str</code> contains lowercase letters that may be separated by a single space.</p>


## Solutions
#### 🐍 Python
```python
class Solution:
    def wordPattern(self, pattern: str, words: str) -> bool:
        d = dict()
        if len(pattern) != len(words.split()):
            return False
        
        for a, b in zip(pattern, words.split()):
            if a in d.keys():
                if d[a] != b:
                    return False
            elif b not in d.values():
                d[a] = b
            else:
                return False
                
        return True
        
        
```
