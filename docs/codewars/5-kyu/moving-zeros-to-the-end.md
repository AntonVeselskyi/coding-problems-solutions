# Moving Zeros To The End

## [Moving Zeros To The End](https://www.codewars.com/kata/52597aa56021e91c93000cb0)

Write an algorithm that takes an array and moves all of the zeros to the end, preserving the order of the other elements.

```javascript
moveZeros([false,1,0,1,2,0,1,3,"a"]) // returns[false,1,1,2,1,3,"a",0,0]
```

```python
move_zeros([False,1,0,1,2,0,1,3,"a"]) # returns[False,1,1,2,1,3,"a",0,0]
```

```coffeescript
moveZeros [false,1,0,1,2,0,1,3,"a"] # returns[false,1,1,2,1,3,"a",0,0]
```

```csharp
Kata.MoveZeroes(new int[] {1, 2, 0, 1, 0, 1, 0, 3, 0, 1}) => new int[] {1, 2, 1, 1, 3, 1, 0, 0, 0, 0}
```

## Solutions

### 🐍 Python

```python
class Zero:
    def __eq__(self, other):
        return other == 0 and other is not False

def move_zeros(array):
    return [i for i in array if i != Zero() ] + [0]*array.count(Zero())
```

