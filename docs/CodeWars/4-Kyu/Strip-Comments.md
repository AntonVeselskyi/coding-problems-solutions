## [Strip Comments](https://www.codewars.com/kata/51c8e37cee245da6b40000bd)

Complete the solution so that it strips all text that follows any of a set of comment markers passed in. Any whitespace at the end of the line should also be stripped out. 

**Example:**

Given an input string of:
```
apples, pears # and bananas
grapes
bananas !apples
```

The output expected would be:
```
apples, pears
grapes
bananas
```

The code would be called like so:

```javascript
var result = solution("apples, pears # and bananas\ngrapes\nbananas !apples", ["#", "!"])
// result should == "apples, pears\ngrapes\nbananas"

```

```kotlin
var result = solution("apples, pears # and bananas\ngrapes\nbananas !apples", charArrayOf('#', '!'))
// result should == "apples, pears\ngrapes\nbananas"

```

```coffeescript
result = solution("apples, pears # and bananas\ngrapes\nbananas !apples", ["#", "!"])
# result should == "apples, pears\nograpes\nbananas"

```

```ruby
result = solution("apples, pears # and bananas\ngrapes\nbananas !apples", ["#", "!"])
# result should == "apples, pears\ngrapes\nbananas"

```

```crystal
result = solution("apples, pears # and bananas\ngrapes\nbananas !apples", ["#", "!"])
# result should == "apples, pears\ngrapes\nbananas"

```

```python
result = solution("apples, pears # and bananas\ngrapes\nbananas !apples", ["#", "!"])
# result should == "apples, pears\ngrapes\nbananas"

```

```csharp
string stripped = StripCommentsSolution.StripComments("apples, pears # and bananas\ngrapes\nbananas !apples", new [] { "#", "!" })
// result should == "apples, pears\ngrapes\nbananas"
```

```julia
result = stripcomments("apples, pears # and bananas\ngrapes\nbananas !apples", ["#", "!"])
# result should == "apples, pears\ngrapes\nbananas"
```

## Solutions
#### 🐍 Python
```python
def solution(string,markers):
    is_comment_section, res, tmp = False, '', ''
    
    for x1 in string.split('\n'):
        for x2 in x1:
            
            if x2 in markers:
                break
            tmp += x2
                
        tmp = tmp.strip() 
        res += tmp +'\n'
        tmp = ''
          
    return res[:-1]
```
