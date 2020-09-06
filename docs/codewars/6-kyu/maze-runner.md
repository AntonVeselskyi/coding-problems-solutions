# Maze Runner

### [Maze Runner](https://www.codewars.com/kata/58663693b359c4a6560001d6)

## Introduction

```text

Welcome Adventurer. Your aim is to navigate the maze and reach the finish point without touching any walls. Doing so will kill you instantly!
```

## Task

```text

You will be given a 2D array of the maze and an array of directions. Your task is to follow the directions given. If you reach the end point before all your moves have gone, you should return Finish. If you hit any walls or go outside the maze border, you should return Dead. If you find yourself still in the maze after using all the moves, you should return Lost.
```

The Maze array will look like

```text
maze = [[1,1,1,1,1,1,1],
        [1,0,0,0,0,0,3],
        [1,0,1,0,1,0,1],
        [0,0,1,0,0,0,1],
        [1,0,1,0,1,0,1],
        [1,0,0,0,0,0,1],
        [1,2,1,0,1,0,1]]
```

..with the following key

```text

      0 = Safe place to walk
      1 = Wall
      2 = Start Point
      3 = Finish Point
```

```c
  directions = "NNNNNEEEEE" == "Finish" // (directions passed as a string)
```

```ruby
  direction = ["N","N","N","N","N","E","E","E","E","E"] == "Finish"
```

```python
  direction = ["N","N","N","N","N","E","E","E","E","E"] == "Finish"
```

```javascript
  direction = ["N","N","N","N","N","E","E","E","E","E"] == "Finish"
```

```php
  direction = ["N","N","N","N","N","E","E","E","E","E"] == "Finish"
```

```csharp
  direction = ["N","N","N","N","N","E","E","E","E","E"] == "Finish"
```

```haskell
  direction = ["N","N","N","N","N","E","E","E","E","E"] == "Finish"
```

## Rules

```text

1. The Maze array will always be square i.e. N x N but its size and content will alter from test to test.

2. The start and finish positions will change for the final tests.

3. The directions array will always be in upper case and will be in the format of N = North, E = East, W = West and S = South.

4. If you reach the end point before all your moves have gone, you should return Finish.

5. If you hit any walls or go outside the maze border, you should return Dead.

6. If you find yourself still in the maze after using all the moves, you should return Lost.
```

Good luck, and stay safe!

## Kata Series

If you enjoyed this, then please try one of my other Katas. Any feedback, translations and grading of beta Katas are greatly appreciated. Thank you.

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Maze Runner](https://www.codewars.com/kata/5866px3693b359c4a6560001d6)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Scooby Doo Puzzle](https://www.codewars.com/kata/58693bbfd7da144164000d05)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/7KYU.png) [Driving License](https://www.codewars.com/kata/586a1af1c66pxd18ad81000134)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Connect 4](https://www.codewars.com/kata/586c0909c1923fdb89002031)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Vending Machine](https://www.codewars.com/kata/586e6d4cb98de09e3800014f)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Snakes and Ladders](https://www.codewars.com/kata/587136ba2eefcb92a9000027)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Mastermind](https://www.codewars.com/kata/58a848258a6909dd35000003)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Guess Who?](https://www.codewars.com/kata/58b2c5de4cf8b90723000051)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Am I safe to drive?](https://www.codewars.com/kata/58f5c63f1e26ecda7e000029)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Mexican Wave](https://www.codewars.com/kata/58f5c63f1e26ecda7e000029)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Pigs in a Pen](https://www.codewars.com/kata/58fdcc51b4f81a0b1e00003e)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Hungry Hippos](https://www.codewars.com/kata/590300eb378a9282ba000095)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Plenty of Fish in the Pond](https://www.codewars.com/kata/5904be220881cb68be00007d)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Fruit Machine](https://www.codewars.com/kata/590adadea658017d90000039)

![](https://raw.githubusercontent.com/adrianeyre/codewars/master/Ruby/Authored/6KYU.png) [Car Park Escape](https://www.codewars.com/kata/591eab1d192fe0435e000014)

### Solutions

#### 🐍 Python

```python
def maze_runner(maze, directions):
    runner_y, runner_x = 0, 0
    print(directions)

    #find start
    for n, row in enumerate(maze):
        if 2 in row:
            runner_y = n
            runner_x = row.index(2)
    for dr in directions:
        if dr == 'N':
            runner_y-=1
        elif dr == 'E':
            runner_x+=1
        elif dr == 'W':
            runner_x-=1
        elif dr == 'S':
            runner_y+=1

        if min(runner_y,runner_x) < 0 or max(runner_y,runner_x) > len(maze)-1 or maze[runner_y][runner_x] == 1:
            return "Dead"
        elif maze[runner_y][runner_x] == 3:
            return "Finish"

    return "Lost"
```

