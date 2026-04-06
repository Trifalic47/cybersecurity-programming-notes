---
id: Pipes
aliases: []
tags: []
---

# DESCRIPTION

 Pipes  and  FIFOs (also known as named pipes) provide a unidirectional interprocess communication channel.  A pipe has a read end and a write end.  Data written to
 the write end of a pipe can be read from the read end of the pipe.

 A pipe is created using pipe(2), which creates a new pipe and returns two file descriptors, one referring to the read end of the pipe, the other referring  to  the
 write end.  Pipes can be used to create a communication channel between related processes; see pipe(2) for an example.

 A FIFO (short for First In First Out) has a name within the filesystem (created using mkfifo(3)), and is opened using open(2).  Any process may open a FIFO, assum‐
 ing  the  file permissions allow it.  The read end is opened using the O_RDONLY flag; the write end is opened using the O_WRONLY flag.  See fifo(7) for further de‐
 tails.  Note: although FIFOs have a pathname in the filesystem, I/O on FIFOs does not involve operations on the underlying device (if there is one).

---

## Pipe Capacity

 A pipe has a limited capacity.  If the pipe is full, then a write(2) will block or fail, depending on whether the O_NONBLOCK flag is set  (see  below).   Different
 implementations  have  different  limits for the pipe capacity.  Applications should not rely on a particular capacity: an application should be designed so that a
 reading process consumes data as soon as it is available, so that a writing process does not remain blocked.

 Before Linux 2.6.11, the capacity of a pipe was the same as the system page size (e.g., 4096 bytes on i386).  Since Linux 2.6.11, the pipe  capacity  is  16  pages
 (i.e.,  65,536  bytes  in a system with a page size of 4096 bytes).  Since Linux 2.6.35, the default pipe capacity is 16 pages, but the capacity can be queried and
 set using the fcntl(2) F_GETPIPE_SZ and F_SETPIPE_SZ operations.  See fcntl(2) for more information.  Since Linux 4.5, the default pipe capacity is lower  than  16
 pages when the pipe-user-pages-soft limit is exceeded.

 The  following  ioctl(2)  operation, which can be applied to a file descriptor that refers to either end of a pipe, places a count of the number of unread bytes in
 the pipe in the int buffer pointed to by the final argument of the call:

---

## Example daily use commands which uses the pipe

```shell
ls | nvim
```

##### Explanation

It will write the `ls` output in the new `nvim` file

See the other notes of this projects on [[Overview]]
