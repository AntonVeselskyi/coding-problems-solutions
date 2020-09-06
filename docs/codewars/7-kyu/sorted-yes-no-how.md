# Sorted? yes? no? how?

## [Sorted? yes? no? how?](https://www.codewars.com/kata/580a4734d6df748060000045)

Complete the method which accepts an array of integers, and returns one of the following:

* `"yes, ascending"` - if the numbers in the array are sorted in an ascending order
* `"yes, descending"` - if the numbers in the array are sorted in a descending order
* `"no"` - otherwise

You can assume the array will always be valid, and there will always be one correct answer.

## Solutions

### 👴 C

```c
enum HowSorted{asc,des};

char* isSortedAndHow(int* array, int length)
{
  enum HowSorted a;
  if(length > 1 && array[0] > array[1])
    a = des;
  else
    a = asc;


  for(int i = 1; i < length-1; ++i)
    { 
      if(a==des)
      {
        if(array[i]<array[i+1])
          return "no";
      }
      else if(a==asc)
      {
        if(array[i]>array[i+1])
          return "no";
      }
    }

  if(a==des)
    return "yes, descending";
  else
    return "yes, ascending";
}
```

