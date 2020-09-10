## [Tortoise racing](https://www.codewars.com/kata/55e2adece53b4cdcb900006c)

Two tortoises named ***A*** and ***B*** must run a race. ***A*** starts with an average speed of ```720 feet per hour```.
Young ***B*** knows she runs faster than ***A***, and furthermore has not finished her cabbage.

When she starts, at last, she can see that ***A*** has a `70 feet lead` but ***B***'s speed is `850 feet per hour`.
How long will it take ***B*** to catch ***A***?

More generally:
given two speeds `v1` (***A***'s speed, integer > 0) and `v2` (***B***'s speed, integer > 0) and a lead `g` (integer > 0)
how long will it take ***B*** to catch ***A***? 

The result will be an array ```[hour, min, sec]``` which is the time needed in hours, minutes and seconds (round down to the nearest second)
or a string in some languages.

If `v1 >= v2` then return `nil`, `nothing`, `null`, `None` or `{-1, -1, -1}` for C++, C, Go, Nim, `[]` for Kotlin or "-1 -1 -1".

## Examples:
(form of the result depends on the language)
```
race(720, 850, 70) => [0, 32, 18] or "0 32 18"
race(80, 91, 37)   => [3, 21, 49] or "3 21 49"
```

** Note: 

- See other examples in "Your test cases".

- In Fortran - as in any other language - the returned string is not permitted to contain any redundant trailing whitespace: you can use dynamically allocated character strings.

** Hints for people who don't know how to convert to hours, minutes, seconds:

- Tortoises don't care about fractions of seconds

- Think of calculation by hand using only integers (in your code use or simulate integer division)

- or Google: "convert decimal time to hours minutes seconds"





## Solutions
#### 👴 C
```c
int* race(int v1, int v2, int g)
{
  int * res = (int*)malloc(sizeof(int)*3);
  if (v1 >= v2)
  {
    res[0]=-1;res[1]=-1;res[2]=-1;
    return res;
  }
  
  double delta_time = 1.0,
  S = g,
  how_long_to_get = 0; //in hours
  while(delta_time > 0.0000000001) // 3.6e-07 sec
  {
    delta_time =  S / (double)v2;
    S = v1 * delta_time;
    how_long_to_get+=delta_time;
  }

  how_long_to_get+=0.00000001;
  res[0] = (int)how_long_to_get; //hours
  res[1] = (how_long_to_get - res[0]) * 60; // mins
  res[2] = (how_long_to_get - res[0] - res[1]/60.0) * 3600; //secs

  return res;
}
```
