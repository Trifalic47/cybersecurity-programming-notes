***

## Use of socket module

*Socket module is used to do networking operations using python.Like we can make TCP server ,we can make an TCP client.Here is an simple example of TCP client using socket in python and OOP(Object Oriented Programming)*.
`But make sure you have an python virtual enviornment and its activated if its not so do python3 -m venv venv and then source vevn/bin/activate`

#### TCP client code
```python
import socket

class Header:
    def __init__(self, host, port=80):
        self._host = host
        self._port = port

    def getHeader(self):
        client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        client.connect((self._host, self._port))
        sendQuery = f"GET / HTTP/1.1\r\nHost: {host}\r\n\r\n"
        client.send(sendQuery.encode())
        response = client.recv(4096)
        return response


if __name__ == "__main__":
    host = "www.google.com"
    port = 80
    header = Header(host, port)
    print(header.getHeader())

```


***
## UDP Client

Next we will make an UDP client but as per the name we will use the UDP network protocol which is faster than TCP but not that much reliable.

Here is the code:
```python
import socket

if __name__ == "__main__":
    host = "127.0.0.1"
    port = 80

    client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

    client.sendto("Are you there?".encode(), (host, port))

    data, addr = client.recvfrom(4096)
    print(data)
```

What happens here is `we do not make an connection before sending the reponse to the server we just directly sends data and specifies the location.`And here we will not get any response from the server so this will be stuck because server is not configured at the host.