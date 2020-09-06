# Linked Lists - Length & Count

## [Linked Lists - Length & Count](https://www.codewars.com/kata/55beec7dd347078289000021)

Linked Lists - Length & Count

Implement Length\(\) to count the number of nodes in a linked list.  


```javascript
length(null) => 0
length(1 -> 2 -> 3 -> null) => 3
```

```csharp
Node.Length(nullptr) => 0
Node.Length(1 -> 2 -> 3 -> nullptr) => 3
```

```cpp
length(null) => 0
length(1 -> 2 -> 3 -> null) => 3
```

Implement Count\(\) to count the occurrences of an integer in a linked list.

```javascript
count(null, 1) => 0
count(1 -> 2 -> 3 -> null, 1) => 1
count(1 -> 1 -> 1 -> 2 -> 2 -> 2 -> 2 -> 3 -> 3 -> null, 2) => 4
```

```csharp
Node.Count(null, value => value == 1) => 0
Node.Count(1 -> 3 -> 5 -> 6, value => value % 2 != 0) => 3
```

```cpp
count(null, 1) => 0
count(1 -> 2 -> 3 -> nullptr, 1) => 1
count(1 -> 1 -> 1 -> 2 -> 2 -> 2 -> 2 -> 3 -> 3 -> nullptr, 2) => 4
```

I've decided to bundle these two functions within the same Kata since they are both very similar.

The `push()`/`Push()` and `buildOneTwoThree()`/`BuildOneTwoThree()` functions do not need to be redefined.

Related Kata in order of expected completion \(increasing difficulty\):  
 [Linked Lists - Push & BuildOneTwoThree](http://www.codewars.com/kata/linked-lists-push-and-buildonetwothree)  
 [Linked Lists - Length & Count](http://www.codewars.com/kata/linked-lists-length-and-count)  
 [Linked Lists - Get Nth Node](http://www.codewars.com/kata/linked-lists-get-nth-node)  
 [Linked Lists - Insert Nth Node](http://www.codewars.com/kata/linked-lists-insert-nth-node)  
 [Linked Lists - Sorted Insert](http://www.codewars.com/kata/linked-lists-sorted-insert)  
 [Linked Lists - Insert Sort](http://www.codewars.com/kata/linked-lists-insert-sort)  
 [Linked Lists - Append](http://www.codewars.com/kata/linked-lists-append)  
 [Linked Lists - Remove Duplicates](http://www.codewars.com/kata/linked-lists-remove-duplicates)  
 [Linked Lists - Move Node](http://www.codewars.com/kata/linked-lists-move-node)  
 [Linked Lists - Move Node In-place](http://www.codewars.com/kata/linked-lists-move-node-in-place)  
 [Linked Lists - Alternating Split](http://www.codewars.com/kata/linked-lists-alternating-split)  
 [Linked Lists - Front Back Split](http://www.codewars.com/kata/linked-lists-front-back-split)  
 [Linked Lists - Shuffle Merge](http://www.codewars.com/kata/linked-lists-shuffle-merge)  
 [Linked Lists - Sorted Merge](http://www.codewars.com/kata/linked-lists-sorted-merge)  
 [Linked Lists - Merge Sort](http://www.codewars.com/kata/linked-lists-merge-sort)  
 [Linked Lists - Sorted Intersect](http://www.codewars.com/kata/linked-lists-sorted-intersect)  
 [Linked Lists - Iterative Reverse](http://www.codewars.com/kata/linked-lists-iterative-reverse)  
 [Linked Lists - Recursive Reverse](http://www.codewars.com/kata/linked-lists-recursive-reverse)  


Inspired by Stanford Professor Nick Parlante's excellent [Linked List teachings.](http://cslibrary.stanford.edu/103/LinkedListBasics.pdf)

## Solutions

### 🧠 C++

```cpp
/* Node Definition
struct Node {
  Node * next;
  int data;
}
*/

int Length(Node *head)
{
  int counter = 0;
  for(;head!=nullptr;head=head->next)
    ++counter;
  return counter;
}

int Count(Node *head, int data)
{
  int counter = 0;
  for(;head!=nullptr;head=head->next)
    if(head->data==data) ++counter;
  return counter;
}
```

