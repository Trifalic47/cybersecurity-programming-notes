---

---
---

***Today we are going to learn that how can we mainipulate the values of the variables using the pointers memory addresses***

---

#### Syntax

```c
#include <stdio.h>

int main(){
    int num = 15;

    // Making an pointer which will hold the memory address of the integer num
    int *numPointer = &num;
    printf("The memory address of the variable num is %p and its value is %d\n",numPointer,num);

    // Changing the value of num by modifying the pointer
    *numPointer = 200;
    printf("The memory address of the variable num is %p and its value is %d\n",numPointer,num);

    return 0;
}
```

## Explanation

*First we did the simple declaration work by `int num =15;` and then get the memory address of the num by `int *numPointer = &num;`. After this we wrote an printf statement to get all the values including memory address of num. Then it comes the main part we did `*numPointer = 200;` , basically what this line did was, it first went to the memoryAddress of the numPointer and got the value inside the numPointer but here we also used `*`,so it will not treat the value as the normal integer, it will treat the value as an memory address and then it goes to memory address present inside the value of the numPointer and then changed its value to 200. *

