# Defanging an IP Address

## [Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address)

Given a valid \(IPv4\) IP `address`, return a defanged version of that IP address.

A _defanged IP address_ replaces every period `"."` with `"[.]"`.

**Example 1:**

```text
Input: address = "1.1.1.1"
Output: "1[.]1[.]1[.]1"
```

**Example 2:**

```text
Input: address = "255.100.50.0"
Output: "255[.]100[.]50[.]0"
```

**Constraints:**

* The given `address` is a valid IPv4 address.

## Solutions

### 🧠 Cpp

```cpp
class Solution {
public:
    string defangIPaddr(string address)
    {
        string res;

        for_each(address.begin(), address.end(),
                [&res](char c) 
                {
                    if(c == '.')
                        res+="[.]";
                    else
                        res.push_back(c);
                });
        return res;
    }
};
```

