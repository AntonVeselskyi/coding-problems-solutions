# SQL with Harry Potter: Sorting Hat Comparators

## [SQL with Harry Potter: Sorting Hat Comparators](https://www.codewars.com/kata/5abcf0f930488ff1a6000b66)

There is truly no magic in the world; the Hogwarts Sorting Hat is SQL-based, its decision-making powers are common operators and prospectIve students are merely data - names, and two columns of qualities.

students

* id
* name
* quality1
* quality2

Slytherin are being quite strict this year and will only take students who are _evil_ AND _cunning_.  
 Gryffindor will take students who are _brave_ but only if their second quality is NOT _evil_.  
 Ravenclaw accepts students who are _studious_ OR _intelligent_.  
 Hufflepuff will simply take those who have the quality _hufflepuff_.

\(don't worry, for simplicity's sake 'brave' and 'studious' will only appear in quality1, and 'cunning' and 'intelligent' will only appear in quality2.\)

Return the _id, name, quality1_ and _quality2_ of all the students who'll be accepted, ordered by ascending id.

## Solutions

### 🗃️ Sql

```sql
select * from students
where ( quality1='evil' and quality2='cunning' )
or ( quality1='brave' and quality2 !='evil' )
or quality1='studious' or quality2='intelligent'
or quality1='hufflepuff' or quality2='hufflepuff';
```
