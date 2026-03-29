
---

Making an function which handles the pipe for the shell programm and the supports argument handling.

#### Programm

```C
void execute_pipe_manual(char *cmd) {
    char beforePipe[100];
    char afterPipe[100];
    int idx = find_index("|",cmd);
    for (int i = 0;i < idx;i++) {
        beforePipe[i] = cmd[i];
    }

    beforePipe[idx] = '\0';

    int k = 0;
    for (int i = idx+1;i < String_Length(cmd);i++){
        afterPipe[k] = cmd[i];
        k++;
    }
    afterPipe[k] = '\0';

    // --- Pipes Logic --------

    int fd[2];
    if (pipe(fd)!=0) {
        print("Error while creating pipe");
        exit(0);
        return;
    }

    char beforeWord[100][100];
    int ch=0,word=0,i=0;
    while (beforePipe[i]) {
        if (beforePipe[0] == ' ')  {
            beforePipe[0] = '\0';
            i++;
        }
        else if (beforePipe[i] == ' ') {
            word++;
            ch = 0;
            i++;
        }else {
            beforeWord[word][ch++] = beforePipe[i];
            i++;
        }
    }
    beforeWord[word][ch] = '\0';

    char afterWord[100][100];
    int ch1=0,word1=0,i1=0;
    while (afterPipe[i1]) {
        if (afterPipe[0] == ' '){
        afterPipe[0] = '\0';
        i1++;
    }
        else if (afterPipe[i1] == ' ') {
            word1++;
            ch1 = 0;
            i1++;
        }
        else {
            afterWord[word1][ch1++] = afterPipe[i1];
            i1++;
        }
    }
    afterWord[word1][ch1] = '\0';
    print(afterWord[0]);
    print("\n");
    print(afterWord[1]);
    print("\n");
    if (fork() == 0) {
        // // --- Child Process: beforePipe-----
        dup2(fd[1],1);
        close(fd[1]);
        close(fd[0]);

        //------------Making argc--------
        char *args[10];
        for (int i = 0; i < word; i++) {
            args[i] = beforeWord[i];
        }
        args[word] = NULL;
        execvp(beforeWord[0],args);
    }
    if (fork() == 0) {
        dup2(fd[0],0);
        close(fd[1]);
        close(fd[0]);

        char *args[10];
        for (int i = 0; i <= word1; i++) {
            args[i] = afterWord[i];
        }
        args[word1 + 1] = NULL;
        execvp(afterWord[0],args);
    }
    //------------Parent Process------
    close(fd[1]);
    close(fd[0]);
    wait(NULL);
    wait(NULL);
}
```

---

## Diagrams Made While Making This Function For Logic

##### Before Pipe and After Pipe Strings Finder

![[Pasted image 20260329202219.png]]

##### Word Counter Programm

![[Pasted image 20260329202428.png]]