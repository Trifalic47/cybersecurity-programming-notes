*** 

## Switch statements in C

-> Switch statements are litte bit like as the if-else statements but are less used nowadays.It is used to prevent complex if else statements.

***Syntax->***
```c
#include <stdio.h>

int main(){
  int option;
  // If the option number is 1 so its true and if its 0 so its false
  printf("Enter the option number:");
  scanf("%d",&option);

  switch (option) {
    case 1:
      printf("Its true");
      break;
    case 0:
      printf("Its false");
      break;
    default:
      printf("Enter an valid option number");
  }

  return 0;
}
```

-> Here first we initialize that on which variable we are going to use switch statements.
