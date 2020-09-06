# Tenth Line

## [Tenth Line](https://leetcode.com/problems/tenth-line)

Given a text file `file.txt`, print just the 10th line of the file.

**Example:**

Assume that `file.txt` has the following content:

```text

Line 1
Line 2
Line 3
Line 4
Line 5
Line 6
Line 7
Line 8
Line 9
Line 10
```

Your script should output the tenth line, which is:

```text

Line 10
```

**Note:**  
 1. If the file contains less than 10 lines, what should you output?  
 2. There's at least three different solutions. Try to explore all possibilities.

## Solutions

### 💲 Bash

```bash
# Read from the file file.txt and output the tenth line to stdout.
if [ $(wc -l file.txt | cut -f1 -d' ') -gt 9 ]
then
    cat file.txt | head -n 10 | tail -n 1
fi
```

