***

#### Using scanf

-> We will use the `scanf()` function to get the input from the user.
***Syntax->***
```c
int age;
scanf("%d",&age);
```

While giving the first argument in the scanf function change the format specifier according to the data type.

***

#### Using fgets to take the character including whitespace

-> We know that scanf does not read the characters after the white space so we can't get the full input from the user.So we are going to use `fgets()` function.

***Syntax->***
```c
char name[50];
printf("Enter your full name:");
fgets(name,sizeof(name),stdin);
```

***

#### Using getchar function to fix some errors and bugs in the code while taking input

-> The main use of the getchar() function in C is to read a single character from the standard input (usually the keyboard) and return it as an integer value representing the ASCII code of that character. It is commonly used for simple input tasks, such as reading characters one by one.

***Get char fixed this buggy code***
```c
#include <stdio.h>

int main() {
  // Taking data as an input from the user
  int age;
  char fav_char;
  char name[30];

  printf("Enter your favourite character:");
  scanf("%c", &fav_char);
  getchar(); // Using getchar to fix the input bug in code

  printf("Enter your full name:");
  fgets(name, sizeof(name), stdin);
  printf("Enter your age here:");
  scanf("%d", &age);

  printf("Welcome %s and you are %d years old.", name, age);

  return 0;
}
```

*** 

## Automatic New line bug fix

-> When we use fgets and takes string as an input it also takes enter as input and stores it as \n(newline) and while printing that string it automatically adds new line and that is an bug in the code. To fix that we will use `<string.h>` C library and use this code line after the string input -- 
```c
buffer[strcspn(buffer,"\n")] = 0;
```