# 80's Kids \#2: Help ALF Find His Spaceship

## [80's Kids \#2: Help ALF Find His Spaceship](https://www.codewars.com/kata/5660aa3d5e011dfd6e000063)

Late last night in the Tanner household, ALF was repairing his spaceship so he might get back to Melmac. Unfortunately for him, he forgot to put on the parking brake, and the spaceship took off during repair. Now it's hovering in space.

ALF has the technology to bring the spaceship home if he can lock on to its location.

Given a map:

```text
..........
..........
..........
.......X..
..........
..........
```

The map will be given in the form of a string with \n separating new lines. The bottom left of the map is \[0, 0\]. X is ALF's spaceship.

In this example:

```javascript
findSpaceship(map) => [7, 2]
```

```coffeescript
findSpaceship(map) => [7, 2]
```

```ruby
find_spaceship(map) => [7, 2]
```

```java
findSpaceship(map) => "[7, 2]"
```

```cpp
findSpaceship(map) => "[7, 2]"
```

If you cannot find the spaceship, the result should be

```text
"Spaceship lost forever."
```

Can you help ALF?

 Check out my other 80's Kids Katas: [80's Kids \#1: How Many Licks Does It Take](http://www.codewars.com/kata/80-s-kids-number-1-how-many-licks-does-it-take)  
 [80's Kids \#2: Help Alf Find His Spaceship](http://www.codewars.com/kata/80-s-kids-number-2-help-alf-find-his-spaceship)  
 [80's Kids \#3: Punky Brewster's Socks](http://www.codewars.com/kata/80-s-kids-number-3-punky-brewsters-socks)  
 [80's Kids \#4: Legends of the Hidden Temple](http://www.codewars.com/kata/80-s-kids-number-4-legends-of-the-hidden-temple)  
 [80's Kids \#5: You Can't Do That on Television](http://www.codewars.com/kata/80-s-kids-number-5-you-cant-do-that-on-television)  
 [80's Kids \#6: Rock 'Em, Sock 'Em Robots](http://www.codewars.com/kata/80-s-kids-number-6-rock-em-sock-em-robots)  
 [80's Kids \#7: She's a Small Wonder](http://www.codewars.com/kata/80-s-kids-number-7-shes-a-small-wonder)  
 [80's Kids \#8: The Secret World of Alex Mack](http://www.codewars.com/kata/80-s-kids-number-8-the-secret-world-of-alex-mack)  
 [80's Kids \#9: Down in Fraggle Rock](http://www.codewars.com/kata/80-s-kids-number-9-down-in-fraggle-rock)  
 [80's Kids \#10: Captain Planet](http://www.codewars.com/kata/80-s-kids-number-10-captain-planet)  


## Solutions

### 🐍 Python

```python
def find_spaceship(astromap):
    for n, i in enumerate(reversed(astromap.split('\n'))):
        if 'X' in i:
            return [i.index('X'),n]
    return "Spaceship lost forever."
```

