*A frequency analyzer is an programm where we find how much time an number repeated in an arary.
Concepts used: **one dimensional arrays**,**for loop**,**if else**,**basic input** * 

---

```C
#include <stdio.h>

int main(){
    int arr[] = {12,3,4,3,5,6,3,2,4,6,7,4,2,1,3,3,5,6,78,2,4,6,7,1,2,3,5,6,7,8,4,2,3,5,6,7,8};
    int size = sizeof(arr) / sizeof(arr[0]);
    int freq[size];

    for (int i=0;i<size;i++) {
        freq[i] = -1;
    }

    for (int i=0;i<size;i++) {
        int count = 1;
        for (int j=i+1;j<size;j++) {
            if(arr[i] == arr[j]) {
                count++;
                freq[j] = 0;
            }
            if (freq[i] != 0) {
                freq[i] = count;
            }
        }
    }

    printf("Element     |       Frequency\n");
    for (int i=0;i<size;i++) {
        if (freq[i] != 0){
                printf("%d      |       %d\n",arr[i],freq[i]);
            }
    }

    return 0;
}
```

#### Explanation: 

*Here you can see that we have used the nested loops and some if else statements and 1d arrays.*

###### Block 1
```C
 int arr[] = {12,3,4,3,5,6,3,2,4,6,7,4,2,1,3,3,5,6,78,2,4,6,7,1,2,3,5,6,7,8,4,2,3,5,6,7,8};
    int size = sizeof(arr) / sizeof(arr[0]);
    int freq[size];

    for (int i=0;i<size;i++) {
        freq[i] = -1;
    }
```

- *In this block of code we defined an array called **arr** which stores all the numbers of which we have to check the frequency.Then we made an variable named **size** which stores the size of arr[] array using the formula `sizeof(arr) / sizeof(arr[0])`*
- *Now we used an for loop.What this loop does is,this sets the value of all the indexes in the **freq** array to **-1**.*

---
###### Block 2

```C
for (int i=0;i<size;i++) {
        int count = 1;
        for (int j=i+1;j<size;j++) {
            if(arr[i] == arr[j]) {
                count++;
                freq[j] = 0;
            }
            if (freq[i] != 0) {
                freq[i] = count;
            }
        }
    }
```

#### Explanation

- *This is the main code block which finds the frequency of numbers.*
- *In the first line we did the initialization of the loop which means it will iterate till `i<size`* 
- *Then we made an integer named count to which we gave the value **-1**.*
- *Now it comes the main part.Here we gave the value of `j=i+1`.So it means the value of j is one more bigger than the value of i and this child loop will iterate till the `j<size` and it will work in increment order which means `i++`.* 
- *Now in the if statement it checks if `arr[i] == arr[j]` which means it is checking if the number is repeating and if its **true** so it will do **count++** and it will assign the `freq[j] = 0`.*
- *In the next if block it checks `if (freq[i] != 0)` which means its checking that if the current value of the freq[i] should not be equal to zero and if it is so `freq[i] = count`.* 


###### Block 3

```C
 printf("Element     |       Frequency\n");
    for (int i=0;i<size;i++) {
        if (freq[i] != 0){
                printf("%d      |       %d\n",arr[i],freq[i]);
            }
    }

    return 0;
```

##### Explanation 

*It is the final most and easiest code block in the whole code.The main usecase of it is that to print the element and the frequency.*

---

## Output 

*So output would come like this* 

```shell
Element     |       Frequency
12     |       1
3      |       7
4      |       5
5      |       4
6      |       6
2      |       5
7      |       4
1      |       2
78     |       1
8      |       2

```

---

Check my repository of C programming at - https://github.com/Trifalic47/cProgramms

