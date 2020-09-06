# Framed Reflection

### [Framed Reflection](https://www.codewars.com/kata/581331293788bc1702001fa6)

## **100th Kata**

You are given a message \(text\) that you choose to read in a mirror \(weirdo\). Return what you would see, complete with the mirror frame. Example:  


'Hello World'

would give:

![](http://res.cloudinary.com/dfvyityr2/image/upload/v1477656440/kata_examp_ypboka.png)

Words in your solution should be left-aligned.

### Solutions

#### 🐍 Python

```python
def mirror(text):
    words=text.split()
    max_w_len = len(max(words))
    topbottom = "*"*(max_w_len+4)+'\n'
    res = topbottom + \
          ''.join([ '* ' + w[::-1] + ' '*(max_w_len-len(w)) + ' *\n' for w in words ]) + \
          topbottom[:-1]
    return res
```

