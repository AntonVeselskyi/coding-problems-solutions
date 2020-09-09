## [Shortest Word](https://www.codewars.com/kata/57cebe1dc6fdc20c57000ac9)

Simple, given a string of words, return the length of the shortest word(s).

String will never be empty and you do not need to account for different data types.


## Solutions
#### 👴 C
```c
#include <sys/types.h>
#include <string.h>

ssize_t find_short(const char *s)
{
  ssize_t min=strlen(s), counter=0;
  for(;;s++)
    if(*s!=' ' && *s!='\0')
      counter++;
    else
    {
      if(min>counter)
        min = counter;
      counter = 0;
      if(*s =='\0')
        break;
    }
  return min;
}
```
