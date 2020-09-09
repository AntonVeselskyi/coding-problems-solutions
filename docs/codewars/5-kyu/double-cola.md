## [Double Cola](https://www.codewars.com/kata/551dd1f424b7a4cdae0001f0)

Sheldon, Leonard, Penny, Rajesh and Howard are in the queue for a "Double Cola" drink vending machine; there are no other people in the queue. The first one in the queue (Sheldon) buys a can, drinks it and doubles! The resulting two Sheldons go to the end of the queue. Then the next in the queue (Leonard) buys a can, drinks it and gets to the end of the queue as two Leonards, and so on. 

For example, Penny drinks the third can of cola and the queue will look like this:
```
Rajesh, Howard, Sheldon, Sheldon, Leonard, Leonard, Penny, Penny
``` 
 
Write a program that will return the name of the person who will drink the `n`-th cola.

## Input:

The input data consist of an array which contains at least 1 name, and single integer `n` which may go as high as the biggest number your language of choice supports (if there's such limit, of course).

## Output / Examples:
Return the single line — the name of the person who drinks the n-th can of cola. The cans are numbered starting from 1. 

~~~if-not:nasm
```rust
let names = &vec![Name::Sheldon, Name::Leonard, Name::Penny, Name::Rajesh, Name::Howard];
assert_eq!(who_is_next(names, 1), Name::Sheldon);
assert_eq!(who_is_next(names, 6), Name::Sheldon);
assert_eq!(who_is_next(names, 52), Name::Penny);
assert_eq!(who_is_next(names, 7230702951), Name::Leonard);
```
```csharp
string[] names = new string[] { "Sheldon", "Leonard", "Penny", "Rajesh", "Howard" };
Line.WhoIsNext(names, 1) == "Sheldon"
Line.WhoIsNext(names, 52) == "Penny"
Line.WhoIsNext(names, 7230702951) == "Leonard"
```
```python
who_is_next(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 1) == "Sheldon"
who_is_next(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 52) == "Penny"
who_is_next(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 7230702951) == "Leonard"
```
```ruby
whoIsNext(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 1) == "Sheldon"
whoIsNext(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 52) == "Penny"
whoIsNext(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 7230702951) == "Leonard"
```
```javascript
whoIsNext(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 1) == "Sheldon"
whoIsNext(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 52) == "Penny"
whoIsNext(["Sheldon", "Leonard", "Penny", "Rajesh", "Howard"], 7230702951) == "Leonard"
```
```kotlin
whoIsNext(listOf("Sheldon", "Leonard", "Penny", "Rajesh", "Howard"), 1) == "Sheldon"
whoIsNext(listOf("Sheldon", "Leonard", "Penny", "Rajesh", "Howard"), 52) == "Penny"
whoIsNext(listOf("Sheldon", "Leonard", "Penny", "Rajesh", "Howard"), 7230702951) == "Leonard"
```
```r
who_is_next(c("Sheldon", "Leonard", "Penny", "Rajesh", "Howard"), 1) == "Sheldon"
who_is_next(c("Sheldon", "Leonard", "Penny", "Rajesh", "Howard"), 52) == "Penny"
who_is_next(c("Sheldon", "Leonard", "Penny", "Rajesh", "Howard"), 10010) == "Howard"
```
```c
char* names[] = {"Sheldon", "Leonard", "Penny", "Rajesh", "Howard"};
who_is_next(names, 5, 1) == "Sheldon"
who_is_next(names, 5, 52) == "Penny"
who_is_next(names, 5, 10010) == "Howard"
```
~~~
~~~if:nasm
```c
char* names[] = { "Sheldon", "Leonard", "Penny", "Rajesh", "Howard" };
who_is_next(1, 5, names) == "Sheldon"
who_is_next(52, 5, names) == "Penny"
who_is_next(7230702951, 5, names) == "Leonard"
```
~~~

##### courtesy of CodeForces: https://codeforces.com/problemset/problem/82/A

## Solutions
#### 🧠 C++
```c++
#include <string>
#include <vector>
#include <cmath>
#include <iostream>

using std::string;
using std::to_string;

std::string who_is_next(std::vector<std::string> names, long long r)
{
  if(r == 1) return names[0]; 
  float clone_counter = 1;
  int queue_size = names.size();
  long long preiter, iter;
  
  if(r > queue_size)
    {
    for(iter = queue_size; iter < r; preiter=iter, iter+=clone_counter*queue_size*2, clone_counter*=2.f );

    int position = (r - preiter); //index of target in the last 'clone' pack (num)
    int res_index = ceil(position/clone_counter)-1;
  
    
    //std::cout << "clones: " <<clone_counter<< "; group_size: " << queue_size << "; howis: " << r << "; left:  " 
    //<< preiter << "; rigth " << iter << "; relative pos:" << position<<  "; prog_chosen_index:" << res_index << '\n';
  
    return names[res_index];
    
    }
  else
    {
      return names[r-1];
    }
  
}

```
