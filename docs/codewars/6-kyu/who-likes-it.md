## [Who likes it?](https://www.codewars.com/kata/5266876b8f4bf2da9b000362)

You probably know the "like" system from Facebook and other pages. People can "like" blog posts, pictures or other items. We want to create the text that should be displayed next to such an item.

Implement a function `likes :: [String] -> String`, which must take in input array, containing the names of people who like an item. It must return the display text as shown in the examples:

```haskell
likes [] -- must be "no one likes this"
likes ["Peter"] -- must be "Peter likes this"
likes ["Jacob", "Alex"] -- must be "Jacob and Alex like this"
likes ["Max", "John", "Mark"] -- must be "Max, John and Mark like this"
likes ["Alex", "Jacob", "Mark", "Max"] -- must be "Alex, Jacob and 2 others like this"
```
```csharp
Kata.Likes(new string[0]) => "no one likes this"
Kata.Likes(new string[] {"Peter"}) => "Peter likes this"
Kata.Likes(new string[] {"Jacob", "Alex"}) => "Jacob and Alex like this"
Kata.Likes(new string[] {"Max", "John", "Mark"}) => "Max, John and Mark like this"
Kata.Likes(new string[] {"Alex", "Jacob", "Mark", "Max"}) => "Alex, Jacob and 2 others like this"
```
```c
* return must be an allocated string
* do not mutate input

likes({})
    // should return "no one likes this"

likes({"Peter"})
    // should return "Peter likes this"

likes({"Jacob", "Alex"})
    // should return "Jacob and Alex like this"

likes({"Max","John","Mark"})
    // should return "Max, John and Mark like this"

likes({"Alex", "Jacob", "Mark", "Max"})
    // should return "Alex, Jacob and 2 others like this"
```
```cpp
likes {} // must be "no one likes this"
likes {"Peter"} // must be "Peter likes this"
likes {"Jacob", "Alex"} // must be "Jacob and Alex like this"
likes {"Max", "John", "Mark"} // must be "Max, John and Mark like this"
likes {"Alex", "Jacob", "Mark", "Max"} // must be "Alex, Jacob and 2 others like this"
```
```java
likes {} // must be "no one likes this"
likes {"Peter"} // must be "Peter likes this"
likes {"Jacob", "Alex"} // must be "Jacob and Alex like this"
likes {"Max", "John", "Mark"} // must be "Max, John and Mark like this"
likes {"Alex", "Jacob", "Mark", "Max"} // must be "Alex, Jacob and 2 others like this"
```
```julia
likes([]) # must be "no one likes this"
likes(["Peter"]) # must be "Peter likes this"
likes(["Jacob", "Alex"]) # must be "Jacob and Alex like this"
likes(["Max", "John", "Mark"]) # must be "Max, John and Mark like this"
likes(["Alex", "Jacob", "Mark", "Max"]) # must be "Alex, Jacob and 2 others like this"
```
```python
likes([]) # must be "no one likes this"
likes(["Peter"]) # must be "Peter likes this"
likes(["Jacob", "Alex"]) # must be "Jacob and Alex like this"
likes(["Max", "John", "Mark"]) # must be "Max, John and Mark like this"
likes(["Alex", "Jacob", "Mark", "Max"]) # must be "Alex, Jacob and 2 others like this"
```

For 4 or more names, the number in `and 2 others` simply increases.


## Solutions
#### 🐍 Python
```python
def likes(names):
    res = []
    if not names:
        return 'no one likes this'
    else:
        count = len(names)
        res = names[0]
        if count == 1:
            res+=" likes this"
        elif count == 2:
            res+=' and '+names[1]+' like this'
        elif count == 3:
            res+=', '+names[1]+" and "+ names[2]+ " like this"
        else:
            res+=', '+names[1]+" and "+str(len(names)-2)+" others like this"
        
    return res
            
    
```
