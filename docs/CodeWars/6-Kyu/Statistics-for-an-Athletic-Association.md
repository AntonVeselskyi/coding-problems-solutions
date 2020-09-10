## [Statistics for an Athletic Association](https://www.codewars.com/kata/55b3425df71c1201a800009c)

You are the "computer expert" of a local Athletic Association (C.A.A.).
Many teams of runners come to compete. Each time you get a string of 
all race results of every team who has run.
For example here is a string showing the individual results of a team of 5 runners:

` "01|15|59, 1|47|6, 01|17|20, 1|32|34, 2|3|17" `

Each part of the string is of the form: ` h|m|s `
where h, m, s (h for hour, m for minutes, s for seconds) are positive or null integer (represented as strings) with one or two digits.
There are no traps in this format.

To compare the results of the teams you are asked for giving
three statistics; **range, average and median**.

`Range` : difference between the lowest and highest values. 
In {4, 6, 9, 3, 7} the lowest value is 3, and the highest is 9, 
so the range is 9 − 3 = 6.

`Mean or Average` : To calculate mean, add together all of the numbers 
in a set and then divide the sum by the total count of numbers.

`Median` : In statistics, the median is the number separating the higher half 
of a data sample from the lower half. 
The median of a finite list of numbers can be found by arranging all 
the observations from lowest value to highest value and picking the middle one 
(e.g., the median of {3, 3, 5, 9, 11} is 5) when there is an odd number of observations. 
If there is an even number of observations, then there is no single middle value; 
the median is then defined to be the mean of the two middle values
(the median of {3, 5, 6, 9} is (5 + 6) / 2 = 5.5).

Your task is to return a string giving these 3 values.  For the example given above,
the string result will be

`"Range: 00|47|18 Average: 01|35|15 Median: 01|32|34"`

of the form:

`"Range: hh|mm|ss Average: hh|mm|ss Median: hh|mm|ss"`

where hh, mm, ss are integers (represented by strings) with *each 2 digits*.

*Remarks*: 

1. if a result in seconds is ab.xy... it will be given **truncated** as ab.

2. if the given string is "" you will return ""


## Solutions
#### 👴 C
```c
#include <string.h>
#include <stdlib.h>

int min(int* a,int s){int res=a[0];for(int i=1;i<s;++i)if(a[i]<res)res=a[i];return res;}
int max(int* a,int s){int res=a[0];for(int i=1;i<s;++i)if(a[i]>res)res=a[i];return res;}
int average(int* a,int s){int res=a[0];for(int i=0;++i && i<s;res+=a[i]);return res/s;}

void sort(int* a,int s){for(int i=0;i<s;++i)for(int j=0;j<s;++j)if(a[i]<a[j])
  {   
    a[i] = a[i]^a[j];
    a[j] = a[i]^a[j];
    a[i] = a[i]^a[j];
  } 
}


char* back_to_hms(int sec)
{
  char* buff = (char*)malloc(sizeof(char)*9);
  int h = sec/3600,
  m = (sec-h*3600)/60,
  s = sec - h*3600 - m*60;
  sprintf(buff,"%02d|%02d|%02d", h,m,s );
  return buff;
}

char* stat(char* strg)
{  
  int *arr = (int*)malloc(sizeof(int)*strlen(strg)/8);
  char indx=0;
  
  //check all hh|mm|ss till the \0
  for(; *strg; strg+=8,++indx)
  {
    if(indx)
        strg+=2;
      
    int hours=atoi(strg), mins=atoi(strg+3), secs=atoi(strg+6);
    arr[indx] = secs + mins*60 + hours*3600;    
  }
  
  int range = max(arr,indx) - min(arr,indx),
  avrg = average(arr,indx);
  sort(arr,indx);
  int median = indx % 2 ? arr[indx/2]  : (arr[indx/2]+arr[indx/2-1])/2 ;
  char *rstr = back_to_hms(range),
  *astr = back_to_hms(avrg),
  *mstr = back_to_hms(median);
  
  
  char* res = (char*)malloc(sizeof(char)*52);
  sprintf(res, "Range: %s Average: %s Median: %s\0", rstr, astr, mstr);
 
  free(arr); 
  free(rstr);
  free(astr);
  free(mstr);
  
  return res;
}
```
