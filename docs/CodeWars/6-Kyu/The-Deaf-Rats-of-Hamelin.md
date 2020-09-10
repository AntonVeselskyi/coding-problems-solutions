## [The Deaf Rats of Hamelin](https://www.codewars.com/kata/598106cb34e205e074000031)

<img src="https://i.imgur.com/ta6gv1i.png?1"/>

---

# Story

The <a href="https://en.wikipedia.org/wiki/Pied_Piper_of_Hamelin">Pied Piper</a> has been enlisted to play his magical tune and coax all the rats out of town.

But some of the rats are deaf and are going the wrong way!

# Kata Task

How many deaf rats are there?

# Legend

* ```P``` = The Pied Piper
* ```O~``` = Rat going left
* ```~O``` = Rat going right

# Example

* ex1 ```~O~O~O~O P``` has 0 deaf rats


* ex2 ```P O~ O~ ~O O~``` has 1 deaf rat


* ex3 ```~O~O~O~OP~O~OO~``` has 2 deaf rats

---

# Series

* [The deaf rats of Hamelin (2D)](https://www.codewars.com/kata/the-deaf-rats-of-hamelin-2d)
</span>

## Solutions
#### 🧠 C++
```c++
int countDeafRats(const std::string &town)
{
    //until we found the PP all the rats that goes to the left is deaf
    //after we dound PP all that foes to the right
    bool found_PP = false;
    int deaf_counter  = 0;
    for(auto iter = town.begin(); iter != town.end(); iter++)
    {
        if(*iter == 'P') found_PP=true;
        
        //going right
        else if(iter[0]=='~' && iter[1]=='O') ++iter , deaf_counter+=found_PP;
        //going left
        else if(iter[0]=='O' && iter[1]=='~') ++iter , deaf_counter+=!found_PP;
    }
    
    return deaf_counter;
}
```
