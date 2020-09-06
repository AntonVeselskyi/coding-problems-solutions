# SQL Basics: Mod

## [SQL Basics: Mod](https://www.codewars.com/kata/594a9592704e4d21bc000131)

Given the following table 'decimals':

 **decimals table schema** 

* id
* number1
* number2

Return a table with one column \(mod\) which is the output of number1 modulus number2.

## Solutions

### 🗃️ Sql

```sql
select number1 % number2 as mod
from decimals;
```

