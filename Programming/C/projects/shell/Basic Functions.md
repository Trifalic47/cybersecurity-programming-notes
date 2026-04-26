
---

# aim

	We are going to make some basic functions like print,print_int,intToStr,StringLength which will help us in the future programms.We are also going to setup our file structure.

---

## Making print function

	Now we are going to make the print function.So here we are going to use the file descriptor 1 -> which is stdout. We can print the text using stdout fd.So to do that we are going to use the function called write().

```C
void print(const char *msg) {
    int len = 0;
    while (msg[len]) len++;
    write(1, msg, len * sizeof(char));
}
```

#### Explanation

	We first made an integer called len which will iterate over loops which will help us write accurate amount of bytes and char in memory.Then we used the while loop which will iterate until msg[len] does not exists and till then len++(increments by one),now len contains the actual length of the message.Now to print we will use syscall called write() and in first parameter we passed file descriptor 1 -> which is stdout:Used for printing. In next parameter we added msg(the thing  which is to be printed) and at the end we added how much bytes we want to allocate and we did len * sizeof(char).



---

# File structure

```
.
├── compile.sh
├── shell
├── shell.c
├── utils.c
└── utils.h
```

---

# file usecase 

	.h files will contain the preprocessor and the libraries importing.It will also include the declaration of the functions.

##### Example utils.h code

```C
#include <unistd.h>
#include <signal.h>
#include <sys/wait.h>

typedef struct Header {
    size_t size;
    int free;
}block_t;

#define HEADER_SIZE sizeof(block_t)

void print(const char *msg);
```

[Full Code](https://github.com/Trifalic47/cProgramms/blob/main/projects/shell/utils.h)

	.c file will contain the actual code -> the functions code and all.

##### Example utils.c code

```C
#include "utils.h"

void print(const char *msg) {
    int len = 0;
    while (msg[len]) len++;
    write(1, msg, len);
}
```

[Full Code](https://github.com/Trifalic47/cProgramms/blob/main/projects/shell/utils.c)


##### shell.c structure

```C
#include "utils.h"

int main() {
	// Your all main programm goes here
	return 0;
}
```
[Full Code](https://github.com/Trifalic47/cProgramms/blob/main/projects/shell/shell.c)

> [!note] All the functions we made in the utils.h and utils.c will be used in main function of the shell.c


##### compile.sh

	compile.sh is an shell script which will compile and run our programm

```bash
#!/bin/bash

gcc -Wall -g -o shell shell.c utils.c
./shell
```

