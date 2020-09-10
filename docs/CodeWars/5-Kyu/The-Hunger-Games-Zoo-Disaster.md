## [The Hunger Games - Zoo Disaster!](https://www.codewars.com/kata/5902bc7aba39542b4a00003d)

<img src="https://i.imgur.com/ta6gv1i.png?1" title="source: imgur.com" />

# Story

A freak power outage at the zoo has caused all of the electric cage doors to malfunction and swing open...

All the animals are out and some of them are eating each other!

# <span style='color:red'>It's a Zoo Disaster!</span>

Here is a list of zoo animals, and what they can eat

* antelope eats grass
* big-fish eats little-fish
* bug eats leaves
* bear eats big-fish
* bear eats bug
* bear eats chicken
* bear eats cow
* bear eats leaves
* bear eats sheep
* chicken eats bug
* cow eats grass
* fox eats chicken
* fox eats sheep
* giraffe eats leaves
* lion eats antelope
* lion eats cow
* panda eats leaves
* sheep eats grass

# Kata Task

### INPUT
A comma-separated string representing all the things at the zoo

### TASK
Figure out who eats whom until no more eating is possible.

### OUTPUT 

A list of strings (refer to the example below) where:
* The first element is the initial zoo (same as INPUT)
* The last element is a comma-separated string of what the zoo looks like when all the eating has finished
* All other elements (2nd to last-1) are of the form ```X eats Y``` describing what happened


# Notes

* Animals can only eat things beside them

* Animals always eat to their **LEFT** before eating to their **RIGHT**

* Always the **LEFTMOST** animal capable of eating will eat before any others

* Any other things you may find at the zoo (which are not listed above) do not eat anything and are not edible


# Example

*Input*

```"fox,bug,chicken,grass,sheep"```

*Working*
<table>
<tr><td>1<td>fox can't eat bug<td><pre>"fox,bug,chicken,grass,sheep"</pre></tr>
<tr><td>2<td>bug can't eat anything<td><pre>"fox,bug,chicken,grass,sheep"</pre></tr>
<tr><td>3<td><span style='color:red'>chicken eats bug</span><td><pre>"fox,chicken,grass,sheep"</pre></tr>
<tr><td>4<td><span style='color:red'>fox eats chicken</span><td><pre>"fox,grass,sheep"</pre></tr>
<tr><td>5<td>fox can't eat grass<td><pre>"fox,grass,sheep"</pre></tr>
<tr><td>6<td>grass can't eat anything<td><pre>"fox,grass,sheep"</pre></tr>
<tr><td>7<td><span style='color:red'>sheep eats grass</span><td><pre>"fox,sheep"</pre></tr>
<tr><td>8<td><span style='color:red'>fox eats sheep</span><td><pre>"fox"</pre></tr>
</table>

*Output*

```["fox,bug,chicken,grass,sheep", "chicken eats bug", "fox eats chicken", "sheep eats grass", "fox eats sheep", "fox"]```






## Solutions
#### 🐍 Python
```python
def who_eats_who(zoo):
    rules = dict(
    antelope=['grass'],
    sheep=['grass'],
    bug=['leaves'],
    giraffe=['leaves'],
    panda=['leaves'],
    bear=['big-fish','bug','chicken','cow','leaves','sheep'],
    chicken=['bug'],
    cow=['grass'],
    fox=['chicken','sheep'],
    lion=['cow','antelope']
    )
    rules['big-fish']=['little-fish']
    
    res_seq = [zoo]
    new_zoo = zoo.split(',')
    someone_died = True
    
    while someone_died:
        someone_died = False
        
        for i, anim in enumerate(new_zoo):
            if anim not in rules.keys():
                continue

            animal_to_eat_indx = None

            if i != 0  and new_zoo[i-1] in rules[anim]:
                animal_to_eat_indx = i-1
            elif i != len(new_zoo)-1 and new_zoo[i+1] in rules[anim]:
                animal_to_eat_indx = i+1

            if animal_to_eat_indx != None:
                res_seq.append("%s eats %s" % (anim, new_zoo[animal_to_eat_indx]) )
                del new_zoo[animal_to_eat_indx]
                someone_died = True
                break      
                
                
            
    res_seq.append(",".join(new_zoo))
    return res_seq
```
