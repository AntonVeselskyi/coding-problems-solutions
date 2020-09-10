## [What time is it?](https://www.codewars.com/kata/57729a09914da60e17000329)

Given a time in AM/PM format as a string, convert it to military (24-hour) time as a string.

Midnight is 12:00:00AM on a 12-hour clock, and 00:00:00 on a 24-hour clock. Noon is 12:00:00PM on a 12-hour clock, and 12:00:00 on a 24-hour clock


Sample Input: 07:05:45PM
Sample Output: 19:05:45

Try not to use built in DateTime libraries.

For more information on military time, check the wiki https://en.wikipedia.org/wiki/24-hour_clock#Military_time

## Solutions
#### 🐍 Python
```python
from datetime import *
#docs: https://www.programiz.com/python-programming/datetime/strptime
def get_military_time(str):
    return datetime.strptime(str, "%I:%M:%S%p").strftime("%H:%M:%S")
```
