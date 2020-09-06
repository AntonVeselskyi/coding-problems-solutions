# Replace With Alphabet Position

## [Replace With Alphabet Position](https://www.codewars.com/kata/546f922b54af40e1e90001da)

Welcome.

In this kata you are required to, given a string, replace every letter with its position in the alphabet.

If anything in the text isn't a letter, ignore it and don't return it.

`"a" = 1`, `"b" = 2`, etc.

## Example

```javascript
alphabetPosition("The sunset sets at twelve o' clock.")
```

```python
alphabet_position("The sunset sets at twelve o' clock.")
```

```ruby
alphabet_position("The sunset sets at twelve o' clock.")
```

```csharp
Kata.AlphabetPosition("The sunset sets at twelve o' clock.")
```

```php
alphabet_position('The sunset sets at twelve o\' clock.');
```

```c
alphabet_position("The sunset sets at twelve o' clock.");
```

```text
text:  db  "The sunset sets at twelve o' clock.",0h0

main:
    mov rdi, text
    call alphabet_position
```

```rust
alphabet_position("The sunset sets at twelve o' clock.")
```

```scala
alphabetPosition("The sunset sets at twelve o' clock.")
```

```groovy
Kata.alphabetPosition("The sunset sets at twelve o' clock.")
```

Should return `"20 8 5 19 21 14 19 5 20 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11"` \(as a string\)

## Solutions

### 🐍 Python

```python
def alphabet_position(text):
    a = ord('a') - 1  #97
    A = ord('A') - 1 #65
    res = ''
    for ch in text:
        if ch.isalpha():
            if ord(ch) > a:
                res+= str(ord(ch) - a)+' '
            else:
                res+= str(ord(ch) - A)+' '

    return res.strip()
```

### 👴 C

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char *alphabet_position(char *text)
{

  //for each char max 2 num code + space
  char* res = (char*)malloc(strlen(text) * sizeof(char) * 3);
  strcpy(res, "");


  if (strlen(text) == 0)
    return res;

  for(int i = 0; i < strlen(text); i++)
  {
    if(isalpha(text[i]))
    {
    //buff - max 4: byte 2 for code 1 for space +1 \n
      char buff[4] = ""; 
      char reducer = (text[i] < 'a' ? 'A' : 'a') - 1;
      printf("%d ", text[i] - reducer );
      sprintf(buff,"%d ", text[i] - reducer );
      strcat(res, buff);
    }
  }

    if(strlen(res) != 0)
      res[strlen(res)-1] = '\0';

    return res;

}
```

