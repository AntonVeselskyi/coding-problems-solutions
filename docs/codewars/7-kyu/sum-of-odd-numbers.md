# Sum of odd numbers

## [Sum of odd numbers](https://www.codewars.com/kata/55fd2d567d94ac3bc9000064)

Given the triangle of consecutive odd numbers:

```text
             1
          3     5
       7     9    11
   13    15    17    19
21    23    25    27    29
...
```

Calculate the row sums of this triangle from the row index \(starting at index 1\) e.g.:

```javascript
rowSumOddNumbers(1); // 1
rowSumOddNumbers(2); // 3 + 5 = 8
```

```ocaml
rowSumOddNumbers 1 (* 1 *)
rowSumOddNumbers 2 (* 3 + 5 = 8 *)
```

```dart
rowSumOddNumbers(1); // 1
rowSumOddNumbers(2); // 3 + 5 = 8
```

```lua
rowSumOddNumbers(1); -- 1
rowSumOddNumbers(2); -- 3 + 5 = 8
```

```php
rowSumOddNumbers(1); // 1
rowSumOddNumbers(2); // 3 + 5 = 8
```

```text
rowSumOddNumbers(1); /* 1 */
rowSumOddNumbers(2); /* 3 + 5 = 8 */
```

```coffeescript
rowSumOddNumbers(1) # 1
rowSumOddNumbers(2) # 3 + 5 = 8
```

```typescript
rowSumOddNumbers(1); // 1
rowSumOddNumbers(2); // 3 + 5 = 8
```

```ruby
row_sum_odd_numbers(1); # 1
row_sum_odd_numbers(2); # 3 + 5 = 8
```

```rust
row_sum_odd_numbers(1); # 1
row_sum_odd_numbers(2); # 3 + 5 = 8
```

```python
row_sum_odd_numbers(1); # 1
row_sum_odd_numbers(2); # 3 + 5 = 8
```

```java
rowSumOddNumbers(1); // 1
rowSumOddNumbers(2); // 3 + 5 = 8
```

```csharp
rowSumOddNumbers(1); // 1
rowSumOddNumbers(2); // 3 + 5 = 8
```

```fsharp
rowSumOddNumbers 1 // 1
rowSumOddNumbers 2 // 3 + 5 = 8
```

```haskell
rowSumOddNumbers 1 -- 1
rowSumOddNumbers 2 -- 3 + 5 = 8
```

```r
row_sum_odd_numbers(1) # 1
[1] 1
row_sum_odd_numbers(2) # 3 + 5
[1] 8
```

```text
mov rdi 1
call row_sum_odd_numbers    ; rax <- 1

mov rdi 2
call row_sum_odd_numbers   ; rax <- 3 + 5
```

```text
(row-sum-odd-numbers 1) # 1
(row-sum-odd-numbers 2) # 3 + 5 = 8
```

```julia
rowsumoddnumbers(1) # 1
rowsumoddnumbers(2) # 3 + 5 = 8
```

```scala
rowSumOddNumbers(1) // 1
rowSumOddNumbers(2) // 3 + 5 = 8
```

```swift
rowSumOddNumbers(1) // 1
rowSumOddNumbers(2) // 3 + 5 = 8
```

```elixir
SumOfOdd.row_sum_odd_numbers(1) // 1
SumOfOdd.row_sum_odd_numbers(2) // 3 + 5 = 8
```

```text
row_sum_odd_numbers(1) % 1
row_sum_odd_numbers(2) % 3 + 5 = 8
```

```text
rowSumOddNumbers(1) // 1
rowSumOddNumbers(2) // 3 + 5 = 8
```

## Solutions

### 👴 C

```c
#include <inttypes.h>

uint64_t rowSumOddNumbers(uint32_t n)
{
    uint32_t row = 1;
    uint64_t num = 1, res = 0;

    for(;row!=n;row++)
      num+=2*row;

    for(int i = 0; i < n; ++i, num+=2)
        res+=num;

    return res;
}
```

