## [Rot13](https://www.codewars.com/kata/530e15517bc88ac656000716)

ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet. ROT13 is an example of the Caesar cipher.

Create a function that takes a string and returns the string ciphered with Rot13. 
If there are numbers or special characters included in the string, they should be returned as they are. Only letters from the latin/english alphabet should be shifted, like in the original Rot13 "implementation".





## Solutions
#### 💲 Shell
```shell
res=''
echo  $1 | grep -o . | 
while read ch
do
  if [[ "$ch" =~ [a-zA-Z] ]]
  then
    
    num_in_alpha=$(printf "%d" "'$ch")
    num_in_alpha=$((num_in_alpha+13))
    
    if [[ "$ch" =~ [a-z] ]]
    then
      
      if ((num_in_alpha > 122))
      then 
        num_in_alpha=$((96 + (num_in_alpha)%122))
      fi
    
    elif [[ "$ch" =~ [A-Z] ]]
    then
    
      if ((num_in_alpha > 90))
      then 
        num_in_alpha=$((64 + (num_in_alpha)%90))
      fi
    fi
    
    new_ch="$(printf "%x" $num_in_alpha )"
    res="$res$(printf "\x$new_ch")"

  else

    if [[ "$res$ch" == "$res" ]]
    then
      res="$res "
    else
      res="$res$ch"
    fi
  
  fi
echo  $res
done


# \xHH   byte with hexadecimal value HH (1 to 2 digits)
# char to ascii value -->  printf "%d" "'$ch"

```
