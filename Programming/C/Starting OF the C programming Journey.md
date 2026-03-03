***

#### Shell script which will run the C programm

```shell
# Compile and run C files with one command
runc() {
    if [[ -f "$1" ]]; then
        # Extract the filename without the .c extension
        local output="${1%.*}"
        
        # Compile the file
        gcc "$1" -o "$output"
        
        # Check if compilation was successful before running
        if [[ $? -eq 0 ]]; then
            ./"$output"
        fi
    else
        echo "Error: File '$1' not found."
    fi
}
```

***
#### Hello world Programm

```c
#include<iostream>

int main(){
	printf("Hello World\n");
	return 0;
}
```
