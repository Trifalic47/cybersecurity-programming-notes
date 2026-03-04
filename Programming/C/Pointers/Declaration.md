
---

**Defination:** *Pointers in C are variables that store the memory address of another variable, allowing for efficient data manipulation and access. They are declared using an asterisk (\*) before the variable name and can be initialized with the address of another variable using the address-of operator (&).*

---

## Declaring an Pointer

*To declare an pointer we will make 2 variables an `int age` to store some data and `int *ptr` to get the memory address of the `int age`*

#### Syntax
```C
int age = 14;
int *ptr = &age;
printf("The memory address of the age variable is:%p",ptr);
```

**NOTE:** *To print the pointer's value we use the %p format specifier not %d*

---

## Meaning of '\*'

*When we define an pointer so we define it like `int *ptr=&num;` .So the '\*' Actually tells to the CPU that dont treat the value inside the **ptr** as normal variable treat it as an **memory address***
