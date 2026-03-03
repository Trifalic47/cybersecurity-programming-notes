***

## File Descriptors

*When we open an new file in our operating system so an new unique entry of that file is made which points to the actual path of the file.File descriptor looks like 1001,4,5,6,7,34,64 means any integeral number.
And note one thing: `file descriptor is made when an file is opened and it gets removed when the file is closed,we can also see the file descriptors currently working in our system by going in /proc/<PID>/fd/.

But when you ls in the fd directory you will see that there is 0,1 and 2 fds'.Actually `0 = stdin` 
`1 = stdout and 2 = stderr`
In depth `stdin` means `standard input` which is resource to take input from user and give it to memory. `stdout` means `standarad output` which helps to print output on our screen.`stderr` means `standarad error` which display errors when there is some misconfiguration.
##### Real life example of stdin stdout and stderr
*Remeber when you type something in the terminal.The terminal uses the resource stdin to take input from you and when it display output so it uses stdout and when there some error comes so it uses stderr resource*

***

## Processes

*In simpler words `an process is a programm running on our operating system.Which means anything which our operating system can read and is currently executing/running is called an process.` For Example: An chrome window opened is also an process,an python programm running is also an process.
Each process has its unique id like 34,53,23,6334,3663 which we call `Integer Process ID or in short PID`.We can also access these processes by their PID's by going in `/proc/` directory.
Here you will see multiple subdirectories and the name will be like 3,34,425.These subdirectories are the processes and you can go inside these subdirectories and can see things about these in depth and also access that which fd's are being used by this process.
![[Pasted image 20260204135844.png]]
Command to access the processes:
You can use the `btop,top,htop or vtop` to see the current running processes but you can also do using commands like:
```shell
ps aux | grep kitty 
```
This will list all the kitty processes.It will look like this:
![[Pasted image 20260204135938.png]]

If you want more easy way to see the current running process so you can run:
```shell
btop
```
It will look like this:
![[Pasted image 20260204140051.png]]

***

## Pseudo Terminals

*Pseudo terminals are used to describe the terminal emulators like gnome shell,kitty,foot,alacritty etc.These terminals  can write into the processes and can edit them.The TTY terminals which are physical and old ones do direct contact with the system's hardware.The pseudo terminals are the virtual terminals which are the modified version of physical terminals(TTY),these provides GUI login screen and other GUIs.*
Tip: TTY terminals can work even the wayland and the os crashes as an backup.You can also accesss them directly using this keybind `Ctrl+Alt+<F1-F6>`
You can also access pseudo terminals session by going in `/dev/pts/<terminalID>`

***

## Inode of an File

*Inode of an file stores FileSize,Permissions,owner and pointer to file block on disk.But note fileName is an metadata which is not included in the inode.*

***

## Cache

*Cache is an  temporary storage in RAM which stores the frequently used file which helps to open them fastly on the next launch.Like you have seen first launch of an application after an reboot takes time to open but if you reopen the same app then it will open immediately because the files of that programm will be stored in cache.*

***

## Devices are also treated as files in linux 

*The devices are also treated as files like if you connected an USB pendrive so it will considered as file and its location will be in `/dev/sda` or other.The USB mouse and keyboard are also saved as `/dev/hidraw , /dev/hidraw1`