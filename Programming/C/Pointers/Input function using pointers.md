
---

*We can make an input function using our pointers knowledge and can take the input from the user.*

***An sinple programm to take int as input***

```C
#include <stdio.h>

void takeInput(int *num);

int main() {
	int num;
	takeInput(&num);
	printf("The value of num is now -> %d\n",num);
	return 0;
}

void takeInput(int *num) {
	printf("Enter the number:");
	scanf("%d",num);
}
```

#### Explanation

*What we did is we have take the memory address of int in the parameters of function which treats the argument's value as an memory address and while giving parameters to the function we gave the parameters as `&num` instead of giving `num` because the `&` tells to give the memory address of the variable instead of variable's value*
